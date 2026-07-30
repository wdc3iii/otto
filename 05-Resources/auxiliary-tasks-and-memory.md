---
type: resource
tags: [rl, navigation, to-revisit]
aliases: [Auxiliary Tasks & Memory, Auxiliary Tasks for Navigation RL, AUX_PREDICTION references]
created: 2026-07-29
modified: 2026-07-29
---

# Auxiliary Tasks & Memory for Navigation RL

> [!note] Agent-maintained reading list, created 2026-07-29. The **grouping and the per-paper takes are
> yours** — lifted from `00-Inbox/AUX_PREDICTION.md` §8, where you noted the bibliographic details were
> verified against arXiv metadata on 2026-07-29. My contribution is the filing, the links, and the
> read-order suggestion.

The literature behind [[auxiliary-prediction-heads]] — the design proposal for adding supervised
prediction heads to the nav policy's recurrent trunk, a workstream under
[[capability-aware-navigation]]. Companion list to [[humanoid-motion-tracking]].

**The question the list serves:** does supervising a recurrent policy make it carry information the
reward gradient doesn't force it to keep — and is that even the right lever, versus changing the
recurrent cell?

**Legend.** `[ ]` unread · ✅ full reading note · 🟨 metadata+abstract stub carrying your verbatim take
· ⬜ no PDF saved · PDF at `attachments/@citekey.pdf` unless marked.
Concepts drafted for this list: [[auxiliary-task-learning]] · [[belief-state]] ·
[[privileged-information]] · [[occupancy-anticipation]].

> [!tip] Suggested read order if you want the argument rather than the catalogue
> **[3] Ye 2020** (the recipe you're copying) → **[1] Mirowski 2017** (why post-GRU) →
> **[9] Occupancy Anticipation** (why mask to unseen) → **[4] Ye 2021** (why visitation ranks highest) →
> **[18] Yang SRU** (the competing hypothesis) → **[24] Ebi** (keep the bookkeeping honest).
> Six papers covers the whole design argument; the rest is support and caution.

---

## 8.1 Auxiliary tasks in navigation RL
- [ ] 🟨 [[@mirowski2017learning]] `[1]` — **Learning to Navigate in Complex Environments** (ICLR 2017). Depth prediction (8-bin classification) + loop-closure binary classification on an A3C nav agent. → [[auxiliary-task-learning]], [[belief-state]]
  - **The two structural findings the whole proposal rests on:** classification > regression, and **depth-from-LSTM (D2) > depth-from-conv (D1)**. Loop closure is proposal #4 in binary form.
- [ ] 🟨 [[@jaderberg2017reinforcement]] `[2]` — **UNREAL** (ICLR 2017). Pixel control, reward prediction, value replay on a shared CNN-LSTM; ~10× speedup on Labyrinth. → [[auxiliary-task-learning]]
  - The origin of the idea. Its replay mechanism is the part on-policy PPO here **cannot cheaply copy**.
- [ ] 🟨 [[@ye2020auxiliary]] `[3]` — **Auxiliary Tasks Speed Up Learning PointGoal Navigation** (CoRL 2020). Inverse dynamics, temporal distance, CPC\|A. 3–5× fewer frames. → [[auxiliary-task-learning]]
  - **The practical recipe, directly portable:** β so each loss term is the same order of magnitude as the PPO loss *at init* (0.1 for ID/CPC\|A, 0.4 for TD), and **subsample aux losses to 10–20% of timesteps**.
- [ ] 🟨 [[@ye2021auxiliary]] `[4]` — **Auxiliary Tasks and Exploration Enable ObjectNav** (ICCV 2021). Six aux tasks, each on its own GRU belief module, attention-fused. → [[auxiliary-task-learning]], [[belief-state]]
  - **Coverage prediction was the largest single contributor** (removing it cost ~2.0% success vs. ~0.3–0.7% for the others) — the closest published analogue of your proposal #4. And: past ~2 aux tasks, go per-task belief modules + attention, not many heads on one 128-unit GRU.
- [ ] ⬜ [[@desai2021auxiliary]] `[5]` — **Auxiliary Tasks for Efficient Learning of Point-Goal Navigation** (WACV 2021). Local scene geometry / transition dynamics / progress toward goal. → [[auxiliary-task-learning]]
  - Independent confirmation of the same three axes; "progress toward the goal" is the family your wavefront-gradient head sits in. **No arXiv version and no PDF saved** — CVF open access, say the word and I'll fetch it.
- [ ] 🟨 [[@gordon2019splitnet]] `[6]` — **SplitNet** (ICCV 2019). RGB/depth/surface-normal decoders off a shared visual encoder. → [[auxiliary-task-learning]], [[sim-to-real-transfer]]
  - Encoder-side, i.e. the part your frozen VAE pretraining already covers. Relevant to the MuJoCo↔Isaac gap, **not** to the GRU.
- [ ] 🟨 [[@ahmed2021self]] `[7]` — **A Self-Supervised Auxiliary Loss for Deep RL in Partially Observable Settings** (2021). Temporal-order classification conditioned on memory; +9.6% on gridworld nav. → [[auxiliary-task-learning]], [[belief-state]]
  - The **cheapest possible** memory-supervising loss — no privileged information at all. A near-free control arm against the privileged-target heads.
- [ ] 🟨 [[@shelhamer2017loss]] `[8]` — **Loss is its own Reward** (ICLR 2017 workshop). → [[auxiliary-task-learning]]
  - Context for why the *choice* of aux target matters more than the count.

## 8.2 Map / geometry / potential-field anticipation as supervised learning
- [ ] 🟨 [[@ramakrishnan2020occupancy]] `[9]` — **Occupancy Anticipation** (ECCV 2020). Occupancy **beyond the visible region** from egocentric RGB-D. → [[occupancy-anticipation]]
  - **The reference for your central design choice** — mask the loss toward cells that are *not* currently visible — plus evidence the unseen region is learnable at useful accuracy.
- [ ] 🟨 [[@ramakrishnan2022poni]] `[10]` — **PONI** (CVPR 2022). Two potential fields on a partial semantic map, one explicitly **geodesic-distance-based**, trained by supervised learning on a passive dataset. → [[occupancy-anticipation]]
  - The closest published precedent for treating **the wavefront field as a supervised target**, and evidence the supervised version is learnable given a decent map.
- [ ] 🟨 [[@chaplot2020learning]] `[11]` — **Active Neural SLAM** (ICLR 2020). Map + pose trained with explicit supervised losses inside an RL loop. → [[occupancy-anticipation]]
  - The canonical "supervise the mapping module, RL only the policy" decomposition — the maximal version of what an aux head does partially.
- [ ] 🟨 [[@shi2026oneocc]] `[12]` — **OneOcc** (CVPR 2026). Semantic occupancy for **legged** robots from one panoramic camera. → [[occupancy-anticipation]], [[traversability-estimation]]
  - Proposals #1+#2 as a standalone perception problem — useful as an **upper bound** on what an aux head could be expected to represent.

## 8.3 Legged robotics: reconstructing privileged information from a recurrent state
- [x] ✅ [[@miki2022learning]] `[13]` — **Learning robust perceptive locomotion** (Science Robotics 2022). *Already in otto.* → [[privileged-information]], [[auxiliary-task-learning]]
  - **The closest existing analogue of this whole proposal:** a 2-layer belief GRU (50 units) with an attention gate on exteroception, decoder reconstructing noiseless height samples + privileged state, `L_bc + 0.5·L_re`. **But the setting is distillation** — the aux loss competes with a BC loss, not a policy gradient. That difference is the main transfer risk.
- [ ] 🟨 [[@nahrendra2023dreamwaq]] `[14]` — **DreamWaQ** (ICRA 2023). CENet: velocity estimation + VAE reconstruction heads trained jointly with the PPO policy that consumes the latent. → [[auxiliary-task-learning]], [[state-estimation]]
  - Precedent for supervised heads sharing a graph with **PPO** rather than with BC — i.e. the setting you're actually in.
- [x] ✅ [[@ji2022concurrent]] `[15]` — **Concurrent Training of a Control Policy and a State Estimator** (RA-L 2022). *Already in otto.* → [[state-estimation]], [[privileged-information]]
  - The same pattern one layer down; evidence the concurrent-supervision recipe is robust enough for hardware.
- [ ] 🟨 [[@ren2024topnav]] `[16]` — **TOP-Nav** (CoRL 2024). Terrain/traversability estimator corrected online by proprioceptive feedback. → [[traversability-estimation]]
  - Proposal #2 as an explicit estimated **module** rather than an aux head — the architectural alternative worth naming when you write up the choice.
- [x] ✅ [[@hoeller2021learning]] `[17]` — **Learning a State Representation and Navigation in Cluttered and Dynamic Environments** (RA-L 2021). *Already in otto.* → [[belief-state]]
  - The RSL lineage leading to `[18]`; representation trained *separately* from the policy.

## 8.4 Memory, POMDPs, privileged information, and cautions
- [x] ✅ [[@yang2025spatially]] `[18]` — **Spatially-Enhanced Recurrent Memory (SRU)** (IJRR 2025). *Already in otto, and already ported in your repo* (`nav/rsl_modules/sru.py`). → [[belief-state]], [[recurrent-navigation-policy]]
  - **The competing hypothesis.** LSTM/GRU/S4/Mamba all handle *temporal* recall but fail at **spatial memorisation across viewpoint change**; fixed inside the cell, **+23.5% over standard RNNs with no auxiliary losses at all**. Run as a parallel arm — if the deficit is inductive bias, no aux target fixes it.
- [ ] 🟨 [[@pasukonis2022evaluating]] `[19]` — **Memory Maze** (2022). Model-free RL plateaus below human on large mazes even with truncated BPTT; reconstruction-based world models do better. → [[belief-state]]
  - **Evidence that reward alone under-trains memory** — the general argument for supervising it — plus a probing methodology close to your `gradient_diagnostic` harness.
- [ ] 🟨 [[@lambrechts2024informed]] `[20]` — **Informed POMDP** (RLC 2024). Training-time information + an objective that learns a **sufficient statistic of the history**. → [[privileged-information]], [[belief-state]]
  - **The theoretical licence** for privileged aux targets: the target may be privileged so long as the policy input is not.
- [ ] 🟨 [[@lambrechts2022recurrent]] `[21]` — **Recurrent networks, hidden states and beliefs in POMDPs** (TMLR 2022). → [[belief-state]]
  - Background for interpreting a `post_rnn` probe — "how much belief is in the hidden state" is precisely what your Step-0 probe measures.
- [ ] 🟨 [[@igl2018deep]] `[22]` — **DVRL** (ICML 2018). Recurrent update as approximate belief inference, with an ELBO shaping the recurrent state. → [[belief-state]], [[world-model]]
  - The model-based end of the same spectrum: supervise memory with a learned generative objective instead of privileged targets.
- [ ] 🟨 [[@guo2018neural]] `[23]` — **Neural Predictive Belief Representations** (2018). CPC vs. CPC\|Action vs. PBL. → [[belief-state]]
  - The source of the PBL objective used in `[4]`, and the analysis of *why* action-conditional prediction beats plain contrastive for belief content.
- [ ] 🟨 [[@ebi2026informed]] `[24]` — **Informed Asymmetric Actor-Critic** (ICML 2026). Arbitrary privileged signals in the **critic** still give unbiased policy gradients. → [[privileged-information]]
  - **Keeps the bookkeeping honest:** your privileged critic map is *unbiased* asymmetry; an actor-side aux head deliberately biases the actor's representation. Different levers — don't conflate them when reporting.
- [ ] 🟨 [[@lyle2021effect]] `[25]` — **On the Effect of Auxiliary Tasks on Representation Dynamics** (AISTATS 2021). → [[auxiliary-task-learning]]
  - The theory argument for choosing **few, well-aligned** targets instead of stacking heads.
- [ ] 🟨 [[@du2018adapting]] `[26]` — **Adapting Auxiliary Losses Using Gradient Similarity** (2018). Gate each aux loss by the cosine between its gradient and the main loss's. → [[auxiliary-task-learning]]
  - The negative-transfer mitigation — and, even if you never gate, **the diagnostic to log from the first run**.

## 8.5 Polar / range-view output parameterisation (context for the radial variant)
- [ ] 🟨 [[@kong2023rethinking]] `[27]` — **RangeFormer** (ICCV 2023). Range-view LiDAR segmentation. → [[occupancy-anticipation]]
  - Evidence a bearing-indexed 2D output is workable — including the seam/discontinuity failure modes your circular-W CNN already faces.
- [ ] 🟨 [[@xue2024pvp]] `[28]` — **PVP** (2024). Polar-representation 3D semantic occupancy. → [[occupancy-anticipation]]
  - Support for the radial target being a *sensible* representation. **Neither `[27]` nor `[28]` uses these as an RL auxiliary** — the radial variant has no direct RL precedent, which is why it's ranked last.

---

## Gap you identified in the literature
The "360 bearings × {class, distance-bin}" target (§3.5 of the source doc) **has no clean RL
precedent**. The closest bodies of work are range-view LiDAR segmentation and polar occupancy
(`[27]`, `[28]`), which establish that polar/range-view is a sane output parameterisation but say
nothing about using it as an RL auxiliary. Aux-in-RL work uses either image-space depth
(`[1]`, `[6]`) or top-down maps (`[4]`, `[9]`). **Treat the radial variant as the higher-variance bet
and the 2D grid as the one with published support.**

## In-repo work these notes build on
Not otto notes — pointers into `legged_locomotion_rl` (branch `nav-simple`, HEAD `ce7e5197`):
`nav.tasks.gradient_diagnostic` (the probe/ceiling harness) · `nav/rsl_modules/sru.py` (port of `[18]`) ·
`nav/rsl_modules/multi_critic_ppo.py` (extension template) ·
`nav/tasks/config/maze_nav/maze_wave_visited_nav.py` (existing "visited cell" channel — nearest in-repo
precedent for proposal #4) · `nav/tasks/encoder_pretraining/wavefront_models.py` + `wavefront_losses.py`
(a supervised wavefront **and gradient** head on the frozen grid encoder, trained to epoch 10/100 on
2026-06-10 and never finished — the offline analogue of the aux head).

## Notes / open decisions
- **Coverage:** 24 of 28 refs are new notes; `[13]`, `[15]`, `[17]`, `[18]` were already in otto and
  are now cross-linked. All new notes are **metadata + verbatim arXiv abstract + your take** — none of
  the 24 has been read in full. Depth is stated in each note.
- **`[5]` Desai & Lee has no PDF** (no arXiv; CVF open access available on request).
- **Promotion candidate:** once §8.1 and §8.4 are read, this plus [[auxiliary-task-learning]] and
  [[belief-state]] is the natural seed for a `learned-memory-for-navigation` MOC in
  [[04-Maps/index|04 · Maps]].
