---
type: paper
citekey: compton2025dynamic
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-07'
authors:
- Compton, William D.
- Csomay-Shanklin, Noel
- Johnson, Cole
- Ames, Aaron D.
year: 2025
venue: ICRA 2025
doi: null
arxiv: '2411.15350'
url: https://arxiv.org/abs/2411.15350
authorship: first
zotero: null
status: read
mine: true
pdf: attachments/@compton2025dynamic.pdf
---

# Dynamic Tube MPC: Learning Tube Dynamics with Massively Parallel Simulation for Robust Safety in Practice

> [!info] Compton, William D.; Csomay-Shanklin, Noel; Johnson, Cole; Ames, Aaron D. · 2025 · ICRA 2025 — **my paper**
> [!info]- otto authors: [[aaron-ames]] · [[noel-csomay-shanklin]]

## TL;DR
Learns an *action-dependent* error tube (how tracking error depends on the planning
model's trajectory) from massively parallel simulation, then plans with a Dynamic Tube
MPC that keeps the (variable-width) tube in free space — trading performance vs. safety
in real time instead of using a single worst-case bound. Demonstrated on the ARCHER 3D
hopper navigating cluttered environments and narrow corridors.

## Problem
Hierarchical safe navigation splits into a [[hierarchical-control|planning layer]] on a
[[reduced-order-model]] and a tracking layer on the full-order dynamics. Tracking error
forces robustification of the plan; the usual [[tube-mpc|tube MPC]] fixes a *worst-case*
tube width, which is conservative because it ignores that some planning trajectories are
easier to track than others.

## Method
### Learning tube dynamics
- Characterize the [[tracking-error-bound|tracking error]] as a function of the planning
  model's actions and an **error history** (the key novelty vs. prior deep-tube work).
- Train on [[massively-parallel-simulation|8192 parallel IsaacGym envs]] → 409,600
  trajectories under shaped random inputs; a quantile ("check") loss makes the learned
  [[dynamic-tube]] an α-quantile bound (α = 0.9). Huber-smoothed L1 penalty.
- Error history (H ≈ 25) sharply reduces Mean Error When Correct (MEC); acts like a
  filter distinguishing states with equal instantaneous error but different error trends.
### Dynamic Tube MPC
- NLP over the planning model: minimize cost s.t. planning dynamics, the learned tube
  dynamics `w = f_wθ(ẽ, z, v)`, and safety `Ball(w)(z) ⊂ C` (circle obstacles buffered
  by tube radius). Solved in CasADi + SNOPT with the NN constraint via L4CasADi at 10 Hz.

## Key results
- Learned recursive tube + long error history modulates aggressiveness: fast in open
  space, slows in narrow corridors to tighten tracking — solving a narrow-gap problem in
  ~200 nodes vs. ~400 for the conservative fixed-tube baseline.
- Deployed on ARCHER hardware for real-time collision-free navigation of clutter and
  narrow gaps — maneuvers infeasible for classic Robust Tube MPC without crippling the
  planning velocity limit.

## Limitations
- Train/eval distribution shift: training trajectories are random, not MPC solutions.
  Mitigated by input shaping + domain randomization; could improve by collecting training
  data with a parallelizable planner in the loop.

## Concepts
- [[reduced-order-model]] · [[tube-mpc]] · [[dynamic-tube]] · [[tracking-error-bound]]
- [[control-barrier-function]] · [[hierarchical-control]] · [[massively-parallel-simulation]]

## Related in otto
> [!note] ai-draft (weekly-review 2026-07-07) — proposed connection, refine/keep as you like.

- [[@roth2025learned]] — **the two poles of one idea.** Both *learn the deployed platform's behavior from massively parallel simulation, then plan against it.* DTMPC quantile-regresses the **tracking error** around a reference (→ gradient MPC); Roth's FDM regresses future **SE(2) pose + failure risk** (→ sampling MPPI). They also share the *identical* limitation, stated in near-identical words — DTMPC: *"training trajectories are random, not MPC solutions"*; Roth: *"only as good as its training distribution."* DTMPC even proposes the fix the FDM line lacks: *collect training data with a parallelizable planner in the loop* (a closed-loop/DAgger idea directly transplantable to an FDM). See [[forward-dynamics-model]].

## My notes
> [!note] (your space) — how this connects to your other work (ZDPs [[@compton2024constructive]],
> robust agility [[@csomayshanklin2024robust]]) and where DTMPC goes next. Fill in your own words.

## Source
- Venue: ICRA 2025. Code: https://github.com/wdc3iii/LearningTubesMPC (ref `code`).
- `doi`/`arxiv` left blank — fill from the published/arXiv version (not fabricated here).

## References (in otto)
- [[@andersson2019casadi]]
- [[@bansal2020deepreach]]
- [[@bradford2019nonlinear]]
- [[@bujarbaruah2019adaptive]]
- [[@chang2019neural]]
- [[@chen2021fastrack]]
- [[@cohen2024safety]]
- [[@compton2024constructive]]
- [[@cosner2024generative]]
- [[@csomayshanklin2022multi]]
- [[@csomayshanklin2023nonlinear]]
- [[@csomayshanklin2024robust]]
- [[@dawson2022safe]]
- [[@do2024tube]]
- [[@fan2020deep]]
- [[@fridovichkeil2017planning]]
- [[@gill2005snopt]]
- [[@girard2009hierarchical]]
- [[@hakobyan2019risk]]
- [[@huber1992robust]]
- [[@kaufmann2023champion]]
- [[@koenker1978regression]]
- [[@kurtz2020robust]]
- [[@langson2004robust]]
- [[@learing2024tubes]]
- [[@li2024reinforcement]]
- [[@liao2024berkeley]]
- [[@lopez2019dynamic]]
- [[@makoviychuk2021isaac]]
- [[@mathiesen2023safety]]
- [[@michel2019design]]
- [[@molnar2022model]]
- [[@paszke2017automatic]]
- [[@pezzato2023sampling]]
- [[@raibert1984experiments]]
- [[@rudin2021learning]]
- [[@salzmann2023real]]
- [[@salzmann2024learning]]
- [[@sieber2021system]]
- [[@tobenkin2010invariant]]
- [[@wabersich2023data]]
- [[@williams2001robust]]
- [[@zhao2021tube]]
