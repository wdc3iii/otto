# Auxiliary prediction heads for the nav policy (GRU-focused)

**Status: research notes / design proposal. Nothing here is implemented.**
Written 2026-07-29. Companion to the wavefront-gradient decodability study
(`nav.tasks.gradient_diagnostic`, branch `nav-simple`) and `NAV_ENVS.md`.

---

## 0. Framing: why this is a different question from the wavefront-gradient probe

The ceiling experiment (2026-07-28, `logs/grad_diagnostic/dwell_ff_standard/mirror_report.json`)
showed that for `ff_standard`, training the *feedforward fusion* explicitly on the
geodesic-gradient objective buys ~0–3° over what RL already produced, and only at long
range. That result is about **one specific attachment point and one specific target**:

* attachment = the **pre-GRU fused latent** (for recurrent policies, the probe's `fused`
  site is the *input* of `memory_a`, so the GRU was never measured);
* target = a quantity that is (mostly) a function of the **current** observation +
  the goal vector.

Both proposed aux families below differ in kind:

1. **Attachment: post-GRU.** Mirowski et al. found depth prediction *from the LSTM output*
   (their D2) consistently beat the same prediction *from the conv output* (D1) — i.e. the
   benefit came from forcing the recurrent state to carry geometry, not from shaping the
   encoder. Our measured ceiling says nothing about that site.
2. **Target: history-dependent.** Occupancy behind the robot, terrain class in a region the
   lidar swept 5 s ago, "have I been here", ground height under an occluded stair tread —
   none of these are computable from the current frame. A head that predicts them can only
   succeed by *storing* them, which is exactly the pressure the reward gradient supplies
   only weakly and only through a 7.2 s BPTT window (§4.4).

The single most important design axis that falls out of this: **supervise the part of the
target that is NOT currently visible.** Predicting the visible part is encoder
reconstruction (the frozen VAE's job, whose ceiling we already measured); predicting the
occluded/behind part is memory. This is the "occupancy anticipation" trick and it should be
a first-class option (per-cell visibility mask) in any implementation, not an afterthought.

---

## 1. Literature

### 1.1 The canonical navigation-RL auxiliary-task results

| Work | Aux tasks | What to take from it |
|---|---|---|
| **Mirowski et al., ICLR 2017**, *Learning to Navigate in Complex Environments* ([arXiv 1611.03673](https://arxiv.org/abs/1611.03673)) | (a) depth prediction from a 4×16 downsampled depth image, as **8-bin classification** (non-uniform bins emphasising far range) rather than regression; (b) **loop-closure** binary classification: was position at *t* near an earlier position *t′*, with an intermediate *t″* far away (thresholds η₁=1, η₂=2 cells) | The two structural findings we care about: **classification > regression** for the geometry target, and **depth-from-LSTM (D2) > depth-from-conv (D1)**. Loss weights swept over β ∈ {1, 3.33, 10}-ish ranges. Loop closure is literally proposal #4. |
| **Jaderberg et al., ICLR 2017 (UNREAL)**, *RL with Unsupervised Auxiliary Tasks* ([arXiv 1611.05397](https://arxiv.org/abs/1611.05397)) | pixel control, reward prediction, value replay on a shared CNN-LSTM | The origin of "aux tasks on a shared recurrent trunk", ~10× learning speedup on Labyrinth. Also the origin of the replay-buffer trick, which on-policy PPO here cannot cheaply copy. |
| **Ye et al., CoRL 2020**, *Auxiliary Tasks Speed Up Learning PointGoal Navigation* ([PMLR v155](https://proceedings.mlr.press/v155/ye21a/ye21a.pdf), [arXiv 2007.04561](https://arxiv.org/abs/2007.04561)) | inverse dynamics, temporal distance (‖j−i‖/T between two frames), CPC\|A (action-conditional contrastive future prediction, secondary GRU unrolled k steps) | 3–5× fewer frames; best agent 5.5× faster to match DD-PPO. **Practical recipe worth copying verbatim:** β chosen so each loss term is the same order of magnitude as the PPO loss *at init* (β=0.1 for ID/CPC\|A, 0.4 for TD); aux losses **subsampled** (0.1–0.2 of timesteps) to bound cost; heads read (visual embedding, belief state hₜ, actions). |
| **Ye, Batra, Das, Wijmans, ICCV 2021**, *Auxiliary Tasks and Exploration Enable ObjectGoal Navigation* ([arXiv 2104.04112](https://arxiv.org/abs/2104.04112)) | 6 tasks: CPC\|A (k=4,16), PBL, action-distribution prediction, generalised inverse dynamics, **coverage prediction** (predicts change in map coverage over k=16 steps, conditioned on voxel visit counts) | Two things. (1) **Coverage prediction was the largest single contributor** in their ablation (removing it cost ~2.0% success vs ~0.3–0.7% for the others) — that is the closest published analogue of proposal #4. (2) With many aux tasks they moved from one shared GRU to **one belief GRU per task, fused by attention** (+ attention-entropy penalty μ≈0.075). If we end up wanting 4 aux heads, this is the architecture to reach for, not 4 heads on one 128-unit GRU. |
| **Desai & Lee, WACV 2021**, *Auxiliary Tasks for Efficient Learning of Point-Goal Navigation* ([CVF](https://openaccess.thecvf.com/content/WACV2021/papers/Desai_Auxiliary_Tasks_for_Efficient_Learning_of_Point-Goal_Navigation_WACV_2021_paper.pdf)) | three tasks targeting **local scene geometry**, **transition dynamics**, and **progress toward the goal** | Independent confirmation of the same three axes; "progress toward the goal" is the family our wavefront-gradient head sits in. |
| **Gordon et al., ICCV 2019 (SplitNet)** ([arXiv 1905.07512](https://arxiv.org/abs/1905.07512)) | RGB / depth / surface-normal decoders off a shared visual encoder | Depth decoding is what buys transfer; the aux heads make the perception trunk *transfer* across simulators. Relevant to our sim2sim gap, but this is encoder-side (the part we already pretrain as a VAE). |
| **Ahmed et al., 2021**, *A Self-Supervised Auxiliary Loss for Deep RL in Partially Observable Settings* ([arXiv 2104.08492](https://arxiv.org/abs/2104.08492)) | classify whether a pair of states from the current episode is in temporal order, conditioned on the agent's memory | Cheapest possible memory-supervising loss (no privileged info at all); +9.6% return on gridworld nav. A useful "free" control arm. |

### 1.2 Map / geometry anticipation as supervised learning

| Work | Relevance |
|---|---|
| **Ramakrishnan, Al-Halah, Grauman, ECCV 2020**, *Occupancy Anticipation* ([arXiv 2008.09285](https://arxiv.org/abs/2008.09285)) | Predicts occupancy **beyond the visible region** from egocentric RGB-D, and shows the anticipated map improves downstream exploration/navigation. This is the reference for the "mask the loss to unseen cells" design and evidence that the unseen part is learnable at useful accuracy. |
| **Ramakrishnan et al., CVPR 2022 (PONI)** ([arXiv 2201.10029](https://arxiv.org/abs/2201.10029)) | Predicts two potential fields on a partial semantic map, one of which is an explicitly **geodesic-distance-based** object potential, trained by **supervised learning on a passive dataset** rather than RL. Direct precedent for "predict the wavefront/geodesic field as a supervised target", and evidence that the supervised version of that target is learnable when the input map is good enough. |
| **Chaplot et al., ICLR 2020 (Active Neural SLAM)** ([arXiv 2004.05155](https://arxiv.org/abs/2004.05155)) | Modular nav where map + pose are trained with **explicit supervised losses** inside an RL loop; the standard reference for "supervise the mapping module, RL only the policy". |
| **OneOcc, 2025** ([arXiv 2511.03571](https://arxiv.org/abs/2511.03571)) | Semantic occupancy prediction for **legged** robots from a single panoramic camera; the modern framing of proposals #1+#2 as a perception task in its own right, including moving toward temporal occupancy sequences. |

### 1.3 Legged robotics: reconstruct-privileged-info is already standard practice

| Work | Relevance |
|---|---|
| **Miki et al., Science Robotics 2022**, *Learning robust perceptive locomotion* ([arXiv 2201.08117](https://arxiv.org/abs/2201.08117)) | **The closest existing analogue of what's being proposed here.** The student's **belief encoder is a 2-layer GRU (50 units)** with an attention gate on exteroception, and a **decoder reconstructs the noiseless height samples + privileged state** (contacts, forces, friction, …). Total loss = `L_bc + 0.5·L_re`. So: a recurrent belief state, supervised to reconstruct a heightmap it cannot see cleanly, at half the weight of the main loss. Their ablation (§S9) shows the gated/reconstructing variant tracks the teacher better under noise. Note the setting is **distillation**, not PPO — the aux loss competes with a BC loss, not a policy gradient. |
| **Nahrendra et al., ICRA 2023 (DreamWaQ)** ([arXiv 2301.10602](https://arxiv.org/abs/2301.10602)) | CENet: one encoder, two supervised heads (body-velocity estimation + VAE reconstruction of the proprio context) trained jointly with the RL policy that consumes the latent. Precedent for "supervised estimator trained concurrently with PPO in the same graph". |
| **Ji et al., RA-L 2022**, *Concurrent Training of a Control Policy and a State Estimator* ([arXiv 2202.05481](https://arxiv.org/abs/2202.05481)) | Same pattern at the locomotion layer: supervised estimator (base lin vel, foot height, contact probability) trained alongside the policy. |
| **Ren et al., CoRL 2024 (TOP-Nav)** ([arXiv 2404.15256](https://arxiv.org/abs/2404.15256)) | Legged nav with an explicit terrain/traversability estimator corrected online by proprioceptive feedback — the "estimate terrain class explicitly" variant of proposal #2, as a module rather than an aux head. |

### 1.4 Memory, POMDPs, and the reasons to be careful

| Work | Relevance |
|---|---|
| **Yang, Frivik, Hoeller, Wang, Cadena, Hutter, 2025**, *Spatially-Enhanced Recurrent Memory for Long-Range Mapless Navigation* ([arXiv 2506.05997](https://arxiv.org/abs/2506.05997)) | **The competing hypothesis, and it is already in this repo** (`nav/rsl_modules/sru.py` implements their SRU cells). They show vanilla LSTM/GRU **fail at spatial memorisation across viewpoint change** (temporal recall is fine), fix it by changing the *cell* (a spatial "star operation"), and report +23.5% over standard RNNs **with no supervised/auxiliary losses at all** — their attention over depth features emerges from RL alone. Directly relevant: if the GRU's failure is an inductive-bias problem, an aux loss is the wrong lever and swapping in the SRU is the right one. These two hypotheses should be tested as parallel arms. |
| **Pasukonis, Lillicrap, Hafner, 2022 (Memory Maze)** ([arXiv 2210.13383](https://arxiv.org/abs/2210.13383)) | Isolates long-term memory in 3D mazes: model-free RL agents plateau well below human on large mazes even with truncated BPTT, while reconstruction-based world models do better. Evidence that reward alone under-trains memory — the general case for supervising it. |
| **Lambrechts, Bolland, Ernst, RLC 2024 (Informed POMDP)** ([arXiv 2306.11488](https://arxiv.org/abs/2306.11488)) | Formalises training-time-only information and gives an objective that uses it to learn a *sufficient statistic of the history*. The theoretical frame for "the aux target may be privileged as long as the policy input isn't". |
| **Ebi, Ernst, Böhm, Lambrechts, 2025/2026**, *Informed Asymmetric Actor-Critic* ([arXiv 2509.26000](https://arxiv.org/abs/2509.26000)) | Privileged signals in the **critic** keep the policy gradient unbiased. Worth stating explicitly: our privileged map already sits in the critic; an aux head is a *different* lever (it biases the actor's representation on purpose), and the two should not be conflated when reporting results. |
| **Lyle, Rowland, Ostrovski, Dabney, AISTATS 2021**, *On the Effect of Auxiliary Tasks on Representation Dynamics* ([arXiv 2102.13089](https://arxiv.org/abs/2102.13089)) | Which aux tasks shape representations usefully, tied to the spectral structure of the transition operator. The theory reference for choosing targets rather than piling them on. |
| **Du, Czarnecki, Jayakumar, Pascanu, Lakshminarayanan, 2018**, *Adapting Auxiliary Losses Using Gradient Similarity* ([arXiv 1812.02224](https://arxiv.org/abs/1812.02224)) | Gate/weight each aux loss by the cosine similarity between its gradient and the main loss's; guarantees convergence to critical points of the main task. The mitigation to reach for if an aux head starts hurting — and cheap to log even if we never gate on it. |

### 1.5 Gap in the literature relevant to the radial idea

The "360 bearings × {class, distance-bin}" target (§3.5) does not have a clean RL precedent I
could find. The closest bodies of work are range-view LiDAR segmentation and polar occupancy
prediction (e.g. [PVP, arXiv 2412.07616](https://arxiv.org/abs/2412.07616); [range-view
segmentation, ICCV 2023](https://openaccess.thecvf.com/content/ICCV2023/papers/Kong_Rethinking_Range_View_Representation_for_LiDAR_Segmentation_ICCV_2023_paper.pdf)),
which establish that polar/range-view is a sane output parameterisation for this data but say
nothing about using it as an RL auxiliary. Aux-in-RL work uses either image-space depth
(Mirowski, SplitNet) or top-down maps (Ye's coverage, occupancy anticipation). So the radial
variant is genuinely novel-ish; treat it as the higher-variance bet and the 2D grid as the
one with published support.

---

## 2. What the literature implies for our five candidate targets

| # | Target | Needs memory? | Published support | Verdict |
|---|---|---|---|---|
| 1 | 2D occupancy grid | Only if masked to unseen cells | Strong (occupancy anticipation, Ye coverage, Miki heightmap) | **Start here** |
| 2 | Terrain class (stair/ramp/door) | Partly (out-of-FOV cells) | Moderate (TOP-Nav, OneOcc, our own seg-encoder work) | Second, folds into #1 as extra channels |
| 3 | Ground heightmap rel. goal height | Yes, in occluded regions | Strong and *specifically legged* (Miki reconstructs exactly this from a GRU) | Cheap add-on to #1 (extra channel) |
| 4 | Visitation / "where I've been" | **Entirely** | Strong (Mirowski loop closure; Ye coverage = biggest ablation delta) | **Highest information-per-parameter for the GRU specifically** |
| 5 | Radial class + distance-to-obstacle bins | Partly | Weak/none as an RL aux | Interesting, do after #1 proves the plumbing |

Two more notes on the set:

* **#4 is the only one that is purely a memory task**, and it is the one whose supervision
  cannot leak into "reconstruct the current frame". If the goal is "force the GRU to hold on
  to something", #4 is the cleanest instrument. It also targets the specific failure the user
  described (circling/backtracking) rather than a proxy for it.
* **Doors don't exist as a label yet.** `NAV_CLASS_NAMES` is
  `{ground, obstacle, stair, ramp, ignore}` ([nav_classes.py:33](nav/meta_terrains/common/nav_classes.py#L33)).
  Two options: (a) derive a *portal/gap* label geometrically from the occupancy grid — a free
  cell whose free neighbourhood is locally narrow (1–2 cells wide) between two larger free
  regions — which needs no terrain-generation change and no cache version bump; (b) stamp a
  real `DOOR` nav class at generation time, which bumps the terrain cache and every derived
  dataset. (a) is the cheap experiment; (b) is the honest label. Recommend (a) first.
* **"Distance to obstacle" is an ESDF**, and the brushfire machinery to produce it already
  exists — `make_wavefront_target` is a brushfire solve; seeding it on obstacle cells instead
  of the goal gives clearance-to-nearest-obstacle for free, on the same lattice.

---

## 3. Target sources already in this repo (no new simulation needed)

| Target | Source | Notes |
|---|---|---|
| Occupancy patch, ego-centric, heading-aligned | [`occupancy_runtime.local_occupancy_patch`](nav/meta_terrains/occupancy_runtime.py#L121) | Already returns `[E, C, C]` float, arbitrary cell count/stride, reads the floor the robot stands on. This is a pure gather → cheap enough to call at update time (§4.3). |
| Occupancy at arbitrary world points | [`occupancy_runtime.sample_occupancy`](nav/meta_terrains/occupancy_runtime.py#L84) | For radial/polar sampling patterns. |
| Geodesic distance + gradient to goal | [`wavefront_runtime`](nav/meta_terrains/wavefront_runtime.py) / [`wavefront_to_goal`](nav/tasks/mdp/wavefront_progress.py#L259) | Already a privileged critic obs. Goal-seeded → **field changes when the goal changes**, so this target cannot be recomputed post-hoc from pose alone. |
| Terrain class per ray | [`terrain_semantics.labels_from_face_ids`](nav/tasks/encoder_pretraining/terrain_semantics.py#L35) + `nav_face_classes` metadata | **Currently offline-only** (used by `scan_generation.py` for the seg-encoder datasets). The runtime fused warp kernel already computes the hit face index `f` from `wp.mesh_query_ray` and discards it ([self_intersection_ray_caster.py:97-110](../legged_locomotion_rl/legged_locomotion_rl/tasks/manager_based/legged_locomotion_rl/mdp/sensors/self_intersection_ray_caster.py#L97)); exposing a per-ray class output is a small kernel + mesh→face-class table change, not a new sensor. |
| Ground height | grid raycaster / height-scan terms used by the `map` obs group | For #3, subtract the goal z to get the "relative to goal height" form. |
| Visitation raster | **Does not exist for the humanoid envs**, but there is a precedent: the 2D toy maze has a per-cell "entered this episode" flag ([`maze_wave_visited_nav.py:253`](nav/tasks/config/maze_nav/maze_wave_visited_nav.py#L253)), fed as a 6th maze-map channel (critic-side). For `Nav-*` this needs a per-env world-frame raster (or a hash set of visited cells) maintained in an event term, reset on episode start, and rendered ego-centrically. |

An important consequence: **every target except the wavefront-derived ones and the visitation
raster is a pure function of `(root_xy, root_z, root_yaw)` plus static terrain.** That
enables the memory-cheap variant in §4.3.

---

## 4. Integration design

### 4.1 Where the aux latent comes from (policy side)

`NavActorCritic` ([nav_actor_critic.py](nav/rsl_modules/nav_actor_critic.py)) already has the
two candidate sites:

```
_actor_features(...)  ->  features          # pre-GRU fused latent  (the site the ceiling
                                           #  experiment already measured)
_head_forward(features, "actor", masks, hidden_state)
    -> memory_a(features, masks, hidden_state).squeeze(0)   # <-- post-GRU, 128-d, NEW site
    -> self.actor(out_mem)
```

([`memory_a` construction :334-337](nav/rsl_modules/nav_actor_critic.py#L334),
[`_head_forward` :619](nav/rsl_modules/nav_actor_critic.py#L619))

Design: have `_head_forward` stash the recurrent output (e.g. `self._last_aux_latent`) when a
flag is set, add `aux_heads: nn.ModuleDict` to the policy, and give the policy a method
`aux_predict() -> dict[str, Tensor]` that the algorithm calls **after** its existing
`policy.act(obs_batch, masks, hidden_state)` in the update loop — no second forward pass, no
duplicated GRU unroll. A `aux_site: {"fused", "post_rnn"}` config field makes the A/B a
one-line cfg change, and lets the non-recurrent tasks use the same code path.

Export is unaffected: the exporter copies only the feature shim + `memory_a.rnn` + `actor`
([nav_actor_critic_exporter.py](nav/rsl_modules/exporters/nav_actor_critic_exporter.py)), so
aux heads never reach JIT/ONNX and have no hardware implication.

### 4.2 Where the loss goes (algorithm side)

Follow the existing extension pattern exactly — `MultiCriticPPO` is the template:

* `nav/rsl_modules/nav_aux_ppo.py`: `class NavAuxPPO(PPO)`, copy `update()` from
  [`multi_critic_ppo.py:81`](nav/rsl_modules/multi_critic_ppo.py#L81), add
  `loss = surrogate + c_v·value − c_e·entropy + Σ_i β_i · L_aux^i`, and extend the returned
  `loss_dict` so each aux term is logged separately (the multi-critic file already
  demonstrates per-channel logging).
* `nav/rsl_modules/nav_aux_runner.py` mirroring `multi_critic_runner.py`.
* `scripts/rsl_rl/train.py` selects the runner by `agent_cfg.class_name`
  ([train.py:287](../../scripts/rsl_rl/train.py#L287)) — one `elif`.

Precedents inside stock rsl_rl worth mimicking: RND adds a loss term with its **own optimizer
and its own obs group** resolved by `resolve_rnd_config`, and the symmetry loss adds a
weighted term to the same `loss`. So both "extra loss on the shared graph" and "extra
obs-group consumed only by a loss" are already blessed patterns.

### 4.3 How targets reach the update (the part that actually matters)

`RolloutStorage` stores the **entire** env observation `TensorDict`
(`rsl_rl/storage/rollout_storage.py:57` in the venv site-packages),
and `recurrent_mini_batch_generator` runs `split_and_pad_trajectories` over that whole
TensorDict with the trajectory masks. `resolve_obs_groups` only *checks* the groups a
consumer names; groups nobody names still ride along.

**Therefore: define aux targets as ordinary observation terms in a new obs group (e.g.
`aux`), list it in no consumer's `obs_groups`, and it arrives in the minibatch already
time-aligned with the BPTT sequences and already carrying `masks_batch`.** No storage
surgery, no new plumbing, and the aux loss automatically respects the padding mask (mask it
exactly the way the value loss is masked).

Two costs to design against:

**(a) VRAM.** At 4096 envs × 36 steps = 147k samples per rollout:

| target per step | bytes | storage per rollout | + padded copy (~1.2–1.5×) |
|---|---|---|---|
| 64×64 f32 | 16 KB | 2.4 GB | ~3–3.6 GB — **no** |
| 64×64 f16 | 8 KB | 1.2 GB | ~1.5–1.8 GB — no |
| 32×32 f16 | 2 KB | 302 MB | ~0.4–0.45 GB — borderline |
| 32×32 uint8 | 1 KB | 151 MB | ~0.2 GB — fine |
| 360 bearings f16 | 720 B | 106 MB | fine |
| pose only (4 floats) | 16 B | 2.4 MB | trivial |

`split_and_pad_trajectories` makes a padded copy of the obs TensorDict, so budget ~2×+ the
raw number, and treat it as unreclaimable (`expandable_segments` has never helped this stack).
Nav runs are already near the VRAM ceiling, so this is a design constraint, not a footnote.

**(b) The pose-recompute alternative.** Because occupancy / height / terrain-class targets are
pure functions of `(root_xy, root_z, root_yaw)` + static terrain (§3), we can store **4 floats
per step** and call `local_occupancy_patch` *inside* `update()` to build the target batch on
the fly (it is a gather, and the same target is rebuilt `num_learning_epochs` × times —
acceptable, or cache per epoch). That turns a 2.4 GB target into 2.4 MB and lets us use a
*fine* grid. This does **not** work for wavefront-derived targets (the field is re-solved on
goal change) or the visitation raster (history-dependent) — those must be stored per step.

### 4.4 The BPTT-horizon problem (specific to #4)

`Nav-*` runs at 5 Hz with `episode_length_s = 45` → ~225 steps per episode, but
`num_steps_per_env = 36` → **the BPTT window is 36 steps ≈ 7.2 s**. rsl_rl carries the hidden
state across rollout boundaries but not the gradient. So a visitation aux head can only teach
the GRU to maintain the raster over ~7 s windows unless the rollout is lengthened (linear
storage cost) — and the interesting circling failures are longer than that.

Mitigations to consider, in increasing cost: (i) make the visitation target *local and recent*
(e.g. "visited within the last N seconds", ego-centric window) so it is learnable inside the
window; (ii) predict the **change** in coverage over the next k steps, which is what Ye's CP
task actually does and is inherently short-horizon; (iii) lengthen `num_steps_per_env`.
Option (i)+(ii) keep the target inside the window and are the honest first experiment; a
"whole-episode visitation" target is partly unlearnable by construction and would read as a
failed aux task for the wrong reason (the same class of methodology bug as the six found in
the gradient probe).

### 4.5 Loss construction details worth fixing up front

* **Weighting:** set each β so the aux term is the same order of magnitude as the PPO loss at
  init (Ye's rule); expect β ~0.1–0.5. Miki's `+0.5·L_re` is the legged-side precedent.
* **Classification over regression** for occupancy/class (Mirowski's D2>D1 finding); for
  heights and distances use discrete bins or a masked smooth-L1, and log a *directional /
  categorical* metric (accuracy, IoU, bin accuracy) rather than raw loss so the numbers are
  interpretable next to the probe's degrees.
* **Masks, three of them:** padding mask (`masks_batch`), validity mask (out-of-grid,
  unreachable, sentinel cells — the defect-6 lesson from the gradient probe: never let a
  saturating normalisation silently drop valid samples), and the **visibility mask** if we go
  after the unseen-region variant.
* **Subsampling:** Ye subsample aux losses to 10–20% of timesteps. With 4 candidate heads on a
  147k-sample rollout that is the difference between free and not.
* **Do not detach** the aux gradient from the trunk — shaping the trunk is the entire point —
  but the frozen lidar/depth encoders stay frozen (they already are; the obs is
  pre-encoded, so aux gradients reach only the fusion + GRU, ~52k params for `ff_standard`
  plus the GRU).
* **Adaptive-KL interaction:** the LR schedule reacts to policy KL only, while the aux
  gradient changes the effective step size on shared parameters. Log grad-norm ratio
  (aux vs PPO) and the cosine similarity between the two gradients from day one — that is
  both the Du et al. diagnostic and the early-warning signal for negative transfer. (This
  stack is already known to be brittle to LR surprises — cf. the adaptive-KL LR not being
  checkpointed, which nukes a converged policy on resume.)
* **Multi-head scaling:** if more than ~2 heads earn their place, switch to Ye's per-task
  belief modules + attention fusion rather than stacking heads on one 128-unit GRU.

---

## 5. Proposed experiment ladder

**Step 0 — probe before training anything (cheap, reuses existing harness).**
The gradient study's whole lesson is that a decodability probe costs hours and a training run
costs days. `gradient_diagnostic/train_probe.py` + `scripts/nav/grad_probe_fit.py` already fit
masked heads on collected latents with env-grouped splits and multi-seed reporting. Extensions
needed: (a) probe the **`post_rnn`** site for a GRU policy — explicitly flagged as untested in
the existing notes; (b) add the new targets (occupancy-behind, visitation, terrain class,
radial clearance) to the collector. Read: *is the information already in the GRU state?* If a
target is already decodable, an aux head on it buys little (the `ff_standard` gradient story);
if it is undecodable *and* the frozen encoder tokens carry it, that's the aux candidate.

**Step 1 — one head, one site.** Occupancy classification (32×32 or finer via pose-recompute),
post-GRU, on the strongest current GRU config, 2 seeds. Report success/SPL-equivalent *and*
the Step-0 probe error, so representation change and behaviour change are separable.

**Step 2 — the unseen-region variant.** Same head, loss masked to cells not currently visible.
This is the test of the memory hypothesis proper; expect it to matter more than Step 1.

**Step 3 — visitation head** (short-horizon / coverage-change form, per §4.4), which is the
one the literature's ablation ranks highest and the one aimed at the actual circling symptom.
Needs a revisit/backtracking metric to evaluate against, not just success rate.

**Step 4 — combine** (per-task belief modules + attention if >2 heads), and add the radial
variant if the 2D grid has paid off.

**Parallel arm, not a later step — SRU.** `sru.py` is already written and wired for the maze
tasks (`ToyMaze-Nav-v2-sru`, `Maze-Wave-Nav-*-sru`) but never run on `Nav-*`. Yang et al.
report their gain over GRU **without any auxiliary loss**, on essentially our task. Running
`Nav-NoMap-masked-*` with `rnn_type="sru_ours"` is a config-level change and is the direct
competitor to this entire workstream; if the GRU's problem is that it cannot align
observations across ego-motion, no aux target fixes that. Run both arms before attributing
any win to supervision.

---

## 6. Risks and open questions

1. **The measured ceiling still applies to the pre-GRU site.** If we attach at `fused`, expect
   ~nothing (that is what the mirror experiment says). Any positive result must be attributed
   to the post-GRU site or to the history-dependence of the target, and the experiment should
   be designed so those two are distinguishable.
2. **Frozen-encoder bottleneck.** The ceiling experiment's conclusion was that the binding
   constraint is the frozen VAE tokens, not the RL objective. If the tokens don't carry stair
   vs ramp, no aux head recovers it — hence Step 0. The masked 54×180 seg-encoder work is the
   relevant upstream lever.
3. **Negative transfer.** Real and documented; the gradient-similarity gate (Du et al.) is the
   mitigation, and logging the two gradient norms is nearly free.
4. **Reward/aux confound.** `wavefront_progress` already supplies dense geodesic shaping. An
   aux head that predicts a wavefront-derived quantity is partially redundant with the reward
   it is meant to help; the occupancy/visitation targets are less entangled.
5. **Doors are not labelled** (§2). Geometric-portal derivation first; a real `DOOR` nav class
   means a terrain-cache bump and dataset regeneration.
6. **Runtime per-ray semantics don't exist yet** in the env (offline only, §3). The radial-class
   target needs the warp kernel to emit face ids — small but real work, and it touches a
   shared sensor used by the locomotion pipeline, so it wants care.
7. **Wall-clock.** Aux heads slow the update, not the rollout (heads are tiny; the extra cost
   is target construction + the extra backward through the trunk). Rollout stays dominant.

---

## 7. One-paragraph recommendation

Probe first (`post_rnn` site, all four candidate targets, existing harness), then implement a
single occupancy head at the post-GRU site with the loss masked to currently-invisible cells,
carried as a non-consumed obs group and recomputed from stored pose to keep VRAM flat. Take the
visitation/coverage head second — it is the one the ObjectNav ablation ranks highest and the
only purely memory-bound target on the list. Run the SRU arm concurrently as the null
hypothesis for "the GRU needs supervision" versus "the GRU needs a better cell". Weight aux
losses by Ye's same-order-of-magnitude-at-init rule, log the aux-vs-PPO gradient cosine from
the first run, and evaluate on a revisit/backtracking metric rather than success rate alone.

---

## 8. References

Grouping mirrors §1. Author lists, titles, venues and journal references were verified against
arXiv metadata on 2026-07-29; where the arXiv title differs from the camera-ready title, both
are given. Numbers in the annotations are the papers' own reported figures.

### 8.1 Auxiliary tasks in navigation RL

**[1] Mirowski, P., Pascanu, R., Viola, F., Soyer, H., Ballard, A. J., Banino, A., Denil, M.,
Goroshin, R., Sifre, L., Kavukcuoglu, K., Kumaran, D., Hadsell, R.** (2017). *Learning to
Navigate in Complex Environments.* ICLR 2017. arXiv:[1611.03673](https://arxiv.org/abs/1611.03673)
(v1 Nov 2016, v3 Jan 2017).
> A3C nav agent + two aux heads: depth prediction from a 4×16 depth image (D1 = regression off
> the conv stack; D2 = 8-bin classification off the top LSTM layer, non-uniform bins
> {0, .05, .175, .3, .425, .55, .675, .8, 1}, single 128-unit MLP → 64 independent 8-way
> softmaxes) and loop-closure binary classification (position at *t* near an earlier *t′* with
> an intermediate *t″* far away; η₁ = 1 cell, η₂ = 2 cells). Loss-weight sweeps β_D1 ∈
> {3.33, 10, 33}, β_D2 ∈ {1, 3.33, 10}, β_L ∈ {1, 3.33, 10}.
> **Take:** classification > regression, and **depth-from-LSTM (D2) > depth-from-conv (D1)** —
> the empirical basis for attaching our heads post-GRU. Loop closure = proposal #4 in binary form.

**[2] Jaderberg, M., Mnih, V., Czarnecki, W. M., Schaul, T., Leibo, J. Z., Silver, D.,
Kavukcuoglu, K.** (2017). *Reinforcement Learning with Unsupervised Auxiliary Tasks* (UNREAL).
ICLR 2017. arXiv:[1611.05397](https://arxiv.org/abs/1611.05397).
> Pixel control, reward prediction and value-function replay on a shared CNN-LSTM trunk with an
> experience-replay buffer. ~10× mean learning speedup on Labyrinth, 880% of human on Atari.
> **Take:** the original "aux tasks on a shared recurrent trunk" result. Its replay mechanism is
> the part on-policy PPO here cannot cheaply copy.

**[3] Ye, J., Batra, D., Wijmans, E., Das, A.** (2020). *Auxiliary Tasks Speed Up Learning
PointGoal Navigation.* CoRL 2020, PMLR v155. arXiv:[2007.04561](https://arxiv.org/abs/2007.04561).
[Code](https://github.com/joel99/habitat-pointnav-aux).
> Three self-supervised aux tasks on a ResNet18 + 512-unit GRU agent: inverse dynamics
> (action from φ_t, φ_{t+1}, h_t; CE; subsample 0.1), temporal distance (|j−i|/T from paired
> embeddings + h_T; MSE; k = 8 pairs), and CPC|A (a *second* GRU unrolled k ∈ {1,2,4,8,16} steps
> on future actions, contrastive CE; subsample 0.2). β = 0.1 (ID, CPC|A), 0.4 (TD), chosen so
> terms are the same order of magnitude at init. 3–5× fewer frames; best agent 5.5× faster to
> DD-PPO's 40 M-frame performance, +0.16 SPL at 40 M.
> **Take:** the loss-weighting rule and the subsampling trick, both directly portable.

**[4] Ye, J., Batra, D., Das, A., Wijmans, E.** (2021). *Auxiliary Tasks and Exploration Enable
ObjectGoal Navigation.* ICCV 2021 (arXiv title: *…Enable ObjectNav*).
arXiv:[2104.04112](https://arxiv.org/abs/2104.04112).
> Six aux tasks — CPC|A (k = 4, 16), PBL [17], action-distribution prediction (KL, k = 6),
> generalised inverse dynamics (CE, k = 4), and **coverage prediction** (change in map coverage
> over k = 16 steps, conditioned on voxel visit counts) — each on its **own GRU belief module**,
> fused by an attention layer conditioned on the observation embedding, with an attention-entropy
> penalty μ = 0.075. 24.5% success / 8.1% SPL on the Habitat ObjectNav challenge (+37% / +8%
> relative). Ablation: removing CP costs ~2.0% success versus ~0.3% (ADP) and ~0.7% (GID).
> **Take:** (a) coverage prediction — our proposal #4 — is the single biggest contributor;
> (b) at >2 aux tasks, go per-task belief module + attention fusion, not many heads on one GRU.

**[5] Desai, S. S., Lee, S.** (2021). *Auxiliary Tasks for Efficient Learning of Point-Goal
Navigation.* WACV 2021, pp. 717–725. IEEE Xplore
[9423043](https://ieeexplore.ieee.org/document/9423043/) ·
[CVF PDF](https://openaccess.thecvf.com/content/WACV2021/papers/Desai_Auxiliary_Tasks_for_Efficient_Learning_of_Point-Goal_Navigation_WACV_2021_paper.pdf).
No arXiv version.
> Three aux tasks targeting **local scene geometry**, **environment transition dynamics** and
> **progress toward the goal**, motivated by the tens-of-millions-of-steps cost of PointNav RL.
> **Take:** independent confirmation of the same three axes; "progress toward the goal" is the
> family our wavefront-gradient head belongs to.

**[6] Gordon, D., Kadian, A., Parikh, D., Hoffman, J., Batra, D.** (2019). *SplitNet: Sim2Sim
and Task2Task Transfer for Embodied Visual Navigation.* ICCV 2019.
arXiv:[1905.07512](https://arxiv.org/abs/1905.07512).
> Decouples perception from policy with RGB / depth / surface-normal decoders on a shared visual
> encoder; depth decoding is what buys sim2sim and task2task transfer.
> **Take:** encoder-side aux (which our frozen VAE pretraining already covers), plus evidence
> that geometry decoders help *transfer* — relevant to the MuJoCo↔Isaac gap, not to the GRU.

**[7] Ahmed, E., Zintgraf, L., Schroeder de Witt, C. A., Usunier, N.** (2021). *A Self-Supervised
Auxiliary Loss for Deep RL in Partially Observable Settings.*
arXiv:[2104.08492](https://arxiv.org/abs/2104.08492).
> Classifier over a pair of states from the current episode plus the agent's memory: are they in
> temporal order? Premise is that temporal order correlates with spatial proximity. +9.6%
> episode reward over a strong baseline on gridworld nav.
> **Take:** the cheapest possible memory-supervising loss — no privileged information at all.
> A good near-free control arm against our privileged-target heads.

**[8] Shelhamer, E., Mahmoudieh, P., Argus, M., Darrell, T.** (2017). *Loss is its own Reward:
Self-Supervision for Reinforcement Learning.* ICLR 2017 workshop.
arXiv:[1612.07307](https://arxiv.org/abs/1612.07307).
> Early systematic comparison of self-supervised aux losses (dynamics, inverse dynamics,
> reconstruction) as substitutes for reward-driven representation learning.
> **Take:** context for why the *choice* of aux target matters more than the count.

### 8.2 Map / geometry / potential-field anticipation as supervised learning

**[9] Ramakrishnan, S. K., Al-Halah, Z., Grauman, K.** (2020). *Occupancy Anticipation for
Efficient Exploration and Navigation.* ECCV 2020.
arXiv:[2008.09285](https://arxiv.org/abs/2008.09285) ·
[project page](https://vision.cs.utexas.edu/projects/occupancy_anticipation/).
> Infers occupancy **beyond the visible region** from egocentric RGB-D by exploiting context in
> both the egocentric view and the accumulated top-down map; the anticipated map then drives
> exploration and navigation, beating strong baselines on Gibson and Matterport3D.
> **Take:** the reference for our central design choice — mask/weight the aux loss toward cells
> that are *not* currently visible — and evidence the unseen region is learnable at useful accuracy.

**[10] Ramakrishnan, S. K., Chaplot, D. S., Al-Halah, Z., Malik, J., Grauman, K.** (2022).
*PONI: Potential Functions for ObjectGoal Navigation with Interaction-free Learning.* CVPR 2022.
arXiv:[2201.10029](https://arxiv.org/abs/2201.10029) ·
[project page](https://vision.cs.utexas.edu/projects/poni/).
> Predicts two potential fields on a partial semantic map — an *area* potential (unexplored
> region) and an **object potential that is explicitly geodesic-distance based** — trained by
> **supervised learning on a passive dataset of top-down maps**, no environment interaction.
> **Take:** the closest published precedent for treating "the wavefront field" as a supervised
> prediction target, and evidence that the supervised version is learnable given a decent map.

**[11] Chaplot, D. S., Gandhi, D., Gupta, S., Gupta, A., Salakhutdinov, R.** (2020). *Learning
to Explore using Active Neural SLAM.* ICLR 2020.
arXiv:[2004.05155](https://arxiv.org/abs/2004.05155) ·
[code](https://github.com/devendrachaplot/Neural-SLAM).
> Modular pipeline whose Neural SLAM module (map + pose) is trained with explicit supervised
> losses inside an RL loop, with RL reserved for the global/local policies.
> **Take:** the canonical "supervise the mapping module, RL only the policy" decomposition — the
> maximal version of what an aux head does partially.

**[12] Shi, H., Wang, Z., Guo, S., Duan, M., Wang, S., Chen, T., Yang, K., Wang, L., Wang, K.**
(2026). *OneOcc: Semantic Occupancy Prediction for Legged Robots with a Single Panoramic Camera.*
CVPR 2026. arXiv:[2511.03571](https://arxiv.org/abs/2511.03571).
> Semantic occupancy prediction targeted specifically at legged/humanoid platforms, moving toward
> temporal occupancy sequences (forecasting future volumes conditioned on past views and actions).
> **Take:** the modern framing of proposals #1+#2 as a standalone perception problem — useful as
> an upper bound on what an aux head could be expected to represent.

### 8.3 Legged robotics: reconstructing privileged information from a recurrent state

**[13] Miki, T., Lee, J., Hwangbo, J., Wellhausen, L., Koltun, V., Hutter, M.** (2022).
*Learning robust perceptive locomotion for quadrupedal robots in the wild.* Science Robotics
7(62), eabk2822. arXiv:[2201.08117](https://arxiv.org/abs/2201.08117) ·
[project page](https://leggedrobotics.github.io/rl-perceptiveloco/).
> **Closest existing analogue to this proposal.** The student's belief encoder is a 2-layer GRU
> (50 units) with an attention gate controlling how much exteroception enters the belief; a
> separate decoder reconstructs the **noiseless height samples** *and* privileged state (contact
> states/forces/normals, friction, external wrenches). Objective `L_bc + 0.5·L_re`. Ablation
> (§S9): gated/reconstructing variants track the teacher better under noise (e.g. action
> divergence 0.690 ± 0.40 vs 0.746 ± 0.40 on rough terrain).
> **Take:** proposals #1/#3 with a published loss weight — but in **distillation**, where the aux
> competes with a BC loss, not a policy gradient. That difference is the main transfer risk.

**[14] Nahrendra, I. M. A., Yu, B., Myung, H.** (2023). *DreamWaQ: Learning Robust Quadrupedal
Locomotion With Implicit Terrain Imagination via Deep Reinforcement Learning.* ICRA 2023.
arXiv:[2301.10602](https://arxiv.org/abs/2301.10602).
> CENet: one encoder with two supervised heads — body linear-velocity estimation and a VAE
> reconstruction of the proprioceptive context — trained jointly with the PPO policy that
> consumes the latent. Validated on Unitree A1.
> **Take:** precedent for supervised heads sharing a graph with PPO (rather than with BC).

**[15] Ji, G., Mun, J., Kim, H., Hwangbo, J.** (2022). *Concurrent Training of a Control Policy
and a State Estimator for Dynamic and Robust Legged Locomotion.* IEEE RA-L 7(2) / ICRA 2022.
arXiv:[2202.05481](https://arxiv.org/abs/2202.05481).
> Policy + supervised state-estimator (base linear velocity, foot height, contact probability)
> trained concurrently; 3.75 m/s flat, 3.54 m/s on a μ = 0.22 plate.
> **Take:** the same pattern one layer down, and evidence the concurrent-supervision recipe is
> robust enough for hardware.

**[16] Ren, J., Liu, Y., Dai, Y., Long, J., Wang, G.** (2024). *TOP-Nav: Legged Navigation
Integrating Terrain, Obstacle and Proprioception Estimation.* CoRL 2024, PMLR v270.
arXiv:[2404.15256](https://arxiv.org/abs/2404.15256).
> Terrain/traversability estimator + waypoint planner + locomotion controller, with online
> correction of the vision-based terrain and obstacle estimates from proprioceptive motion
> feedback.
> **Take:** proposal #2 (terrain class) realised as an explicit estimated module rather than an
> aux head — the architectural alternative worth naming when we write up the choice.

**[17] Hoeller, D., Wellhausen, L., Farshidian, F., Hutter, M.** (2021). *Learning a State
Representation and Navigation in Cluttered and Dynamic Environments.* IEEE RA-L 6(3), 5081–5088.
arXiv:[2103.04351](https://arxiv.org/abs/2103.04351).
> Fuses an image sequence + camera trajectory into a learned world model via state-representation
> learning; the representation is trained to estimate the hidden state of the world and to help
> bridge the reality gap, then fed to an RL target-reaching/obstacle-avoiding policy.
> **Take:** the RSL lineage that leads to [19]; representation trained separately from the policy.

### 8.4 Memory, POMDPs, privileged information, and cautions

**[18] Yang, F., Frivik, P., Hoeller, D., Wang, C., Cadena, C., Hutter, M.** (2025).
*Spatially-Enhanced Recurrent Memory for Long-Range Mapless Navigation via End-to-End
Reinforcement Learning.* IJRR 2025, [doi:10.1177/02783649251401926](https://doi.org/10.1177/02783649251401926).
arXiv:[2506.05997](https://arxiv.org/abs/2506.05997) (v1 title: *Improving Long-Range Navigation
with Spatially-Enhanced Recurrent Memory…*).
> **The competing hypothesis, and already implemented in this repo** (`nav/rsl_modules/sru.py`
> ports their §4.4 cells). Shows LSTM/GRU/S4/Mamba all handle *temporal* recall but fail at
> **spatial memorisation across viewpoint change**; fixes it inside the recurrent cell with a
> spatial-transform "star operation" (SRU), plus spatial attention to compress feature maps, TC-
> Dropout and Deep Mutual Learning. +23.5% over standard RNNs, +29.6% over an explicit-mapping
> baseline, zero-shot sim-to-real. **No supervised or auxiliary losses at all** — their attention
> over obstacles/free space emerges from RL.
> **Take:** run this as a parallel arm. If the GRU's deficit is inductive bias, no aux target
> fixes it, and we would be attributing an SRU-shaped win to supervision.

**[19] Pasukonis, J., Lillicrap, T., Hafner, D.** (2022). *Evaluating Long-Term Memory in 3D
Mazes* (Memory Maze). arXiv:[2210.13383](https://arxiv.org/abs/2210.13383) ·
[project page](https://danijar.com/project/memorymaze/) ·
[code](https://github.com/jurgisp/memory-maze).
> Benchmark isolating long-term memory (object positions, wall layout, self-localisation) from
> exploration. Model-free agents with truncated BPTT solve 9×9 but fall far short of humans on
> 15×15; reconstruction-based world models do better; includes an offline probing protocol.
> **Take:** evidence that reward alone under-trains memory — the general argument for supervising
> it — and a probing methodology close to our `gradient_diagnostic` harness.

**[20] Lambrechts, G., Bolland, A., Ernst, D.** (2024). *Informed POMDP: Leveraging Additional
Information in Model-Based RL.* Reinforcement Learning Conference / RLJ 2024 (earlier version at
the ICML 2023 workshop on New Frontiers in Learning, Control, and Dynamical Systems).
arXiv:[2306.11488](https://arxiv.org/abs/2306.11488).
> Formalises the *informed POMDP*: training-time information *i* such that the observation is
> conditionally independent of the state given *i*, with an objective that uses it to learn a
> **sufficient statistic of the history**; demonstrated as an informed world model in Dreamer.
> **Take:** the theoretical licence for privileged aux targets — the aux target may be privileged
> so long as the policy input is not.

**[21] Lambrechts, G., Bolland, A., Ernst, D.** (2022). *Recurrent networks, hidden states and
beliefs in partially observable environments.* TMLR 2022.
arXiv:[2208.03520](https://arxiv.org/abs/2208.03520).
> Studies empirically how well RNN hidden states in model-free RL approximate belief states.
> **Take:** background for interpreting a `post_rnn` probe result — "how much belief is in the
> hidden state" is precisely what our Step-0 probe measures.

**[22] Igl, M., Zintgraf, L., Le, T. A., Wood, F., Whiteson, S.** (2018). *Deep Variational
Reinforcement Learning for POMDPs.* ICML 2018.
arXiv:[1806.02426](https://arxiv.org/abs/1806.02426).
> Structures the recurrent update as approximate belief inference, with a generative model and an
> auxiliary (ELBO) loss shaping the recurrent state.
> **Take:** the model-based end of the same spectrum — supervise the memory with a learned
> generative objective instead of privileged targets.

**[23] Guo, Z. D., Azar, M. G., Piot, B., Pires, B. A., Munos, R.** (2018/2019). *Neural
Predictive Belief Representations.* arXiv:[1811.06407](https://arxiv.org/abs/1811.06407).
> Compares CPC, CPC|Action and PBL-style predictive objectives for learning belief
> representations in partially observed environments.
> **Take:** the source of the PBL objective used in [4], and the analysis of *why*
> action-conditional prediction beats plain contrastive prediction for belief content.

**[24] Ebi, D., Ernst, D., Böhm, K., Lambrechts, G.** (2026). *Informed Asymmetric Actor-Critic:
Leveraging Privileged Signals Beyond Full-State Access.* ICML 2026.
arXiv:[2509.26000](https://arxiv.org/abs/2509.26000).
> Shows arbitrary state-dependent privileged signals in the **critic** still give unbiased policy
> gradients, and gives two criteria for selecting informative signals; carefully chosen partial
> signals match or beat full-state asymmetric baselines.
> **Take:** keeps the bookkeeping honest — our privileged critic map is *unbiased* asymmetry,
> whereas an actor-side aux head deliberately biases the actor's representation. Different levers;
> do not conflate them when reporting.

**[25] Lyle, C., Rowland, M., Ostrovski, G., Dabney, W.** (2021). *On the Effect of Auxiliary
Tasks on Representation Dynamics.* AISTATS 2021, PMLR v130.
arXiv:[2102.13089](https://arxiv.org/abs/2102.13089).
> Connects the spectral decomposition of the transition operator to the representations induced by
> different aux tasks, and uses that to inform aux-task selection in sparse-reward settings.
> **Take:** the theory argument for choosing few, well-aligned targets instead of stacking heads.

**[26] Du, Y., Czarnecki, W. M., Jayakumar, S. M., Farajtabar, M., Pascanu, R.,
Lakshminarayanan, B.** (2018). *Adapting Auxiliary Losses Using Gradient Similarity.*
arXiv:[1812.02224](https://arxiv.org/abs/1812.02224).
> Weight/gate each aux loss by the cosine similarity between its gradient and the main loss's
> (thresholded or proportional); guaranteed convergence to critical points of the main task.
> Validated on multi-task ImageNet subsets, gridworld RL and Atari.
> **Take:** the negative-transfer mitigation, and — even if we never gate — the diagnostic to log
> from the first run.

### 8.5 Polar / range-view output parameterisation (context for the radial variant)

**[27] Kong, L., Liu, Y., Chen, R., Ma, Y., Zhu, X., Li, Y., Hou, Y., Qiao, Y., Liu, Z.** (2023).
*Rethinking Range View Representation for LiDAR Segmentation* (RangeFormer). ICCV 2023.
arXiv:[2303.05367](https://arxiv.org/abs/2303.05367).
> Range-view (spherical-projection) LiDAR segmentation, addressing the spatial discontinuity and
> contextual sparsity that make naive range-view models underperform voxel methods.
> **Take:** evidence that a bearing-indexed 2D output is a workable parameterisation for our lidar
> — including the failure modes (seam/discontinuity handling) our circular-W CNN already faces.

**[28] Xue, Y., Liu, J., Du, J., Zhou, J. T.** (2024). *PVP: Polar Representation Boost for 3D
Semantic Occupancy Prediction.* arXiv:[2412.07616](https://arxiv.org/abs/2412.07616).
> Polar-coordinate occupancy prediction, motivated by polar's alignment with the uneven radial
> distribution of LiDAR geometry/semantics.
> **Take:** support for the radial target being a *sensible* representation. Note that neither
> [27] nor [28] uses these as RL auxiliary tasks — for the radial variant (§3.5) there is no
> direct RL precedent, which is why it is ranked after the 2D-grid heads.

### 8.6 In-repo work these notes build on

* `nav.tasks.gradient_diagnostic` (branch `nav-simple`, HEAD `ce7e5197`) — the probe +
  mirror/ceiling harness whose result frames §0; final numbers in
  `logs/grad_diagnostic/dwell_ff_standard/mirror_report.json`.
* `nav/rsl_modules/sru.py` — this repo's port of [18].
* `nav/rsl_modules/multi_critic_ppo.py`, `multi_critic_runner.py` — the extension template for §4.2.
* `nav/tasks/config/maze_nav/maze_wave_visited_nav.py` — the existing "visited cell" channel
  (toy maze, obs-side rather than aux-side); the nearest in-repo precedent for proposal #4.
* `nav/tasks/encoder_pretraining/` — `wavefront_models.py` / `wavefront_losses.py` already
  implement a supervised wavefront **and gradient** head on the frozen grid encoder
  (`predict_gradient`, `w_gradient`), trained once to epoch 10/100 on 2026-06-10 and never
  finished. That is the offline analogue of the aux head discussed here.
