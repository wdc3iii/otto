---
type: project
tags: [navigation, rl, open-question]
aliases: [Auxiliary prediction heads, AUX_PREDICTION, aux heads for the nav policy]
status: active
created: 2026-07-29
modified: 2026-07-29
repo: /home/wcompton/repos/legged_locomotion_rl
source: 00-Inbox/AUX_PREDICTION.md
---

# Auxiliary prediction heads for the nav policy (GRU-focused)

> [!abstract] Status — **research notes / design proposal. Nothing here is implemented.**
> Your own design doc, written 2026-07-29, ingested into otto the same day. Companion to the
> wavefront-gradient decodability study (`nav.tasks.gradient_diagnostic`, branch `nav-simple`) and
> `NAV_ENVS.md`. A workstream under [[capability-aware-navigation]] → *Nav policy architecture &
> training*.
>
> **Provenance:** distilled from `00-Inbox/AUX_PREDICTION.md` (638 lines, kept in place as the source
> of record). Everything below is **your reasoning and your decisions** unless explicitly marked as my
> inference. The full §4 integration design, VRAM tables, and file-level line references live in the
> source doc — this note carries the argument, the decisions, and the links into otto.

## The question
Does adding a **supervised prediction head** to the nav policy's recurrent trunk make the GRU carry
information it currently drops? See [[auxiliary-task-learning]].

## Why this is a different question from the wavefront-gradient probe
The ceiling experiment (2026-07-28, `logs/grad_diagnostic/dwell_ff_standard/mirror_report.json`) found
that training the feedforward fusion on the geodesic-gradient objective buys **~0–3°** over what RL
already produced, and only at long range. Your point is that this result is narrow — it constrains
**one attachment point and one target**:

- **attachment** = the *pre-GRU* fused latent (the probe's `fused` site is the *input* of `memory_a`, so
  the GRU was never measured);
- **target** = a quantity that is mostly a function of the current observation + the goal vector.

Both proposed aux families differ in kind. Attachment: **post-GRU** — [[@mirowski2017learning]] found
depth prediction from the LSTM output beat the same prediction from the conv output, i.e. the benefit
came from forcing the recurrent state to carry geometry. Target: **history-dependent** — occupancy
behind the robot, terrain class the lidar swept 5 s ago, "have I been here" — none computable from the
current frame, so a head predicting them can only succeed by *storing* them.

> [!important] The design axis that falls out of this (your words)
> **Supervise the part of the target that is NOT currently visible.** Predicting the visible part is
> encoder reconstruction (the frozen VAE's job, whose ceiling we already measured); predicting the
> occluded/behind part is memory. This is the "occupancy anticipation" trick and it should be a
> first-class option (per-cell visibility mask) in any implementation, not an afterthought.

→ [[occupancy-anticipation]], [[belief-state]]

## The five candidate targets, with your verdicts

| # | Target | Needs memory? | Published support | Your verdict |
|---|---|---|---|---|
| 1 | 2D occupancy grid | Only if masked to unseen cells | Strong — [[@ramakrishnan2020occupancy]], [[@ye2021auxiliary]], [[@miki2022learning]] | **Start here** |
| 2 | Terrain class (stair/ramp/door) | Partly (out-of-FOV cells) | Moderate — [[@ren2024topnav]], [[@shi2026oneocc]] | Second; folds into #1 as extra channels |
| 3 | Ground heightmap rel. goal height | Yes, in occluded regions | Strong *and specifically legged* — [[@miki2022learning]] reconstructs exactly this from a GRU | Cheap add-on to #1 (extra channel) |
| 4 | Visitation / "where I've been" | **Entirely** | Strong — [[@mirowski2017learning]] loop closure; [[@ye2021auxiliary]] coverage = biggest ablation delta | **Highest information-per-parameter for the GRU specifically** |
| 5 | Radial class + distance-to-obstacle bins | Partly | Weak/none as an RL aux | Interesting; after #1 proves the plumbing |

Your two notes on the set:
- **#4 is the only purely-memory target**, and the only one whose supervision cannot leak into
  "reconstruct the current frame." It also targets the observed failure (circling/backtracking) rather
  than a proxy for it.
- **Doors aren't labelled.** `NAV_CLASS_NAMES` is `{ground, obstacle, stair, ramp, ignore}`. Either
  (a) derive a *portal/gap* label geometrically from the occupancy grid — no terrain-cache bump — or
  (b) stamp a real `DOOR` class at generation time, which bumps the cache and every derived dataset.
  **You recommend (a) first**: cheap experiment now, honest label later.
- **"Distance to obstacle" is an ESDF** and the machinery exists — `make_wavefront_target` is a
  brushfire solve; seeding it on obstacle cells instead of the goal gives clearance for free on the
  same lattice.

## Decisions already made
1. **Probe before training.** Extend the existing `gradient_diagnostic` harness to the **`post_rnn`**
   site and the new targets. A decodability probe costs hours; a training run costs days. If a target
   is already decodable, an aux head on it buys little.
2. **Attach post-GRU, not at `fused`.** The measured ceiling applies to the pre-GRU site; attaching
   there should be expected to do ~nothing.
3. **Mask the loss to currently-invisible cells** — the memory hypothesis proper, expected to matter
   more than the unmasked version.
4. **Carry targets as a non-consumed obs group.** Define aux targets as ordinary observation terms in
   a new `aux` group listed in no consumer's `obs_groups`; they then arrive in the minibatch already
   time-aligned with the BPTT sequences and carrying `masks_batch`. No storage surgery.
5. **Recompute from stored pose to keep VRAM flat.** Occupancy/height/terrain-class targets are pure
   functions of `(root_xy, root_z, root_yaw)` + static terrain, so store 4 floats/step and rebuild the
   target inside `update()` — turns a 2.4 GB target into 2.4 MB and permits a *fine* grid. Does **not**
   work for wavefront-derived targets (field re-solves on goal change) or visitation (history-dependent).
6. **Weight by Ye's rule** — each $\beta$ so the aux term is the same order of magnitude as the PPO
   loss at init; expect $\beta \sim 0.1$–$0.5$ ([[@ye2020auxiliary]]; [[@miki2022learning]]'s
   $+0.5\,\mathcal{L}_{re}$ is the legged-side precedent).
7. **Classification over regression** for occupancy/class ([[@mirowski2017learning]]'s D2>D1), and log
   an interpretable categorical metric (accuracy/IoU) rather than raw loss.
8. **Three masks, not one** — padding (`masks_batch`), validity (out-of-grid/unreachable/sentinel: the
   defect-6 lesson from the gradient probe — never let a saturating normalisation silently drop valid
   samples), and visibility.
9. **Log the aux-vs-PPO gradient cosine from day one** — both the [[@du2018adapting]] diagnostic and
   the early-warning signal for negative transfer.
10. **Run the SRU arm concurrently, not later.** See below.

## The experiment ladder
**Step 0** — probe the `post_rnn` site with all four candidate targets on the existing harness.
**Step 1** — one head, one site: occupancy classification, post-GRU, strongest current GRU config, 2 seeds. Report success *and* the Step-0 probe error so representation change and behaviour change stay separable.
**Step 2** — the unseen-region variant (loss masked to invisible cells). The real test.
**Step 3** — visitation head, short-horizon/coverage-change form. Needs a **revisit/backtracking metric**, not just success rate.
**Step 4** — combine; per-task belief modules + attention if >2 heads ([[@ye2021auxiliary]]); add the radial variant if the 2D grid paid off.

> [!warning] Parallel arm, not a later step — the SRU null hypothesis (your framing)
> `sru.py` is already written and wired for the maze tasks but never run on `Nav-*`.
> [[@yang2025spatially]] report **+23.5% over standard RNNs with no auxiliary loss at all**, on
> essentially this task, and show LSTM/GRU fail specifically at *spatial* memorisation across viewpoint
> change. Running `Nav-NoMap-masked-*` with `rnn_type="sru_ours"` is a config-level change and is the
> **direct competitor to this entire workstream**. If the GRU's problem is that it cannot align
> observations across ego-motion, no aux target fixes it. Run both arms before attributing any win to
> supervision.

## The BPTT-horizon problem (specific to #4)
`Nav-*` runs at 5 Hz with `episode_length_s = 45` (~225 steps/episode) but `num_steps_per_env = 36` →
**the BPTT window is ~7.2 s**. rsl_rl carries the hidden state across rollout boundaries but not the
gradient, so a visitation head can only teach the GRU to maintain the raster over ~7 s — and the
interesting circling failures are longer than that. Your mitigations, in increasing cost: (i) make the
target *local and recent*; (ii) predict the **change** in coverage over the next $k$ steps (what
[[@ye2021auxiliary]]'s CP task actually does, inherently short-horizon); (iii) lengthen
`num_steps_per_env`.

Your judgement: (i)+(ii) are the honest first experiment, because a whole-episode visitation target is
**partly unlearnable by construction** and would read as a failed aux task for the wrong reason — "the
same class of methodology bug as the six found in the gradient probe."

## Risks and open questions
1. The measured ceiling still applies to the pre-GRU site — any positive result must be attributable to
   the post-GRU site *or* to target history-dependence, and the design must keep those distinguishable.
2. **Frozen-encoder bottleneck.** If the frozen VAE tokens don't carry stair-vs-ramp, no aux head
   recovers it. Hence Step 0. The masked 54×180 seg-encoder work is the upstream lever.
3. **Negative transfer** — real and documented; [[@du2018adapting]] is the mitigation.
4. **Reward/aux confound.** `wavefront_progress` already supplies dense geodesic shaping, so a head
   predicting a wavefront-derived quantity is partly redundant with the reward it's meant to help.
   Occupancy/visitation are less entangled.
5. Doors not labelled; 6. runtime per-ray semantics don't exist yet (offline only, and the warp kernel
   is shared with the locomotion pipeline, so it wants care); 7. wall-clock cost lands on the update,
   not the rollout.

## One-paragraph recommendation (your words, condensed)
Probe first (`post_rnn`, all four targets, existing harness), then implement a **single occupancy head
at the post-GRU site with the loss masked to currently-invisible cells**, carried as a non-consumed obs
group and recomputed from stored pose to keep VRAM flat. Take the **visitation/coverage head second** —
highest-ranked in the ObjectNav ablation and the only purely memory-bound target. Run the **SRU arm
concurrently** as the null hypothesis for "the GRU needs supervision" vs. "the GRU needs a better
cell." Weight by Ye's same-order-at-init rule, log the aux-vs-PPO gradient cosine from the first run,
and evaluate on a **revisit/backtracking metric** rather than success rate alone.

## Concepts
- [[auxiliary-task-learning]] — the mechanism, and the attachment-point/target-history axes.
- [[belief-state]] — what a post-GRU head is trying to shape; the supervision-vs-inductive-bias fork.
- [[occupancy-anticipation]] — the visibility-masking design choice, decision #3.
- [[privileged-information]] — why the privileged critic map and an actor-side aux head are
  **different levers** ([[@ebi2026informed]]) and must not be conflated when reporting.
- [[recurrent-navigation-policy]] · [[mapless-navigation]] · [[traversability-estimation]]

## Reading list
[[auxiliary-tasks-and-memory]] — all 28 references, grouped as in your §8.

## Open threads for me
- The **revisit/backtracking metric** (Step 3) doesn't exist yet and isn't specified in the doc. It
  gates Step 3 and is probably worth defining before Step 1, so Step 1 can log it as a baseline.
- *My inference, flagged:* decisions #1 (probe first) and #10 (SRU as a parallel arm) together imply a
  cheap third arm — probe the **SRU's** hidden state at `post_rnn` too. If the SRU already carries the
  visitation/occupancy information the GRU lacks, that settles the fork before either training run.
