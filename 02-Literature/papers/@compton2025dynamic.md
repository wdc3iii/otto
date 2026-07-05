---
type: paper
citekey: compton2025dynamic
tags: [control, rl, locomotion]
aliases: [Dynamic Tube MPC, DTMPC]
created: 2026-07-05
modified: 2026-07-05
authors:
  - Compton, William D.
  - Csomay-Shanklin, Noel
  - Johnson, Cole
  - Ames, Aaron D.
year: 2025
venue: "ICRA 2025 (IEEE Int. Conf. on Robotics and Automation)"
doi:
arxiv:
url:
zotero:
status: read
mine: true
---

# Dynamic Tube MPC: Learning Tube Dynamics with Massively Parallel Simulation for Robust Safety in Practice

> [!info] Compton, Csomay-Shanklin, Johnson, Ames · 2025 · ICRA — **my paper** (first author)

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

## My notes
> [!note] (your space) — how this connects to your other work (ZDPs [[@compton2024]],
> robust agility [[@csomay2024robust]]) and where DTMPC goes next. Fill in your own words.

## Source
- Venue: ICRA 2025. Code: https://github.com/wdc3iii/LearningTubesMPC (ref `code`).
- `doi`/`arxiv` left blank — fill from the published/arXiv version (not fabricated here).

## References (in otto)

- [[@koenker1978regression]] — Koenker et al. (1978) — Regression quantiles
- [[@raibert1984experiments]] — Raibert et al. (1984) — Experiments in balance with a 3D one-legged hopping machine
- [[@huber1992robust]] — Huber (1992) — Robust estimation of a location parameter
- [[@williams2001]] — Williams et al. (2001) — Robust Sampling Based Model Predictive Control with Sparse Objective I
- [[@langson2004]] — Langson et al. (2004) — Robust model predictive control using tubes
- [[@gill2005snopt]] — Gill et al. (2005) — SNOPT: An SQP algorithm for large-scale constrained optimization
- [[@girard2009]] — Girard et al. (2009) — Hierarchical control system design using approximate simulation
- [[@tobenkin2010]] — Tobenkin et al. (2010) — Invariant Funnels around Trajectories using Sum-of-Squares Programming
- [[@frido2017]] — Fridovich-Keil et al. (2017) — Planning, Fast and Slow: A Framework for Adaptive Real-Time Safe Traje
- [[@paszke2017automatic]] — Paszke et al. (2017) — Automatic differentiation in PyTorch
- [[@andersson2019]] — Andersson et al. (2019) — CasADi -- A software framework for nonlinear optimization and optimal 
- [[@bradford2019]] — Bradford et al. (2019) — Nonlinear model predictive control with explicit back-offs for Gaussia
- [[@bujarbaruah2019]] — Bujarbaruah et al. (2019) — Adaptive MPC under Time Varying Uncertainty: Robust and Stochastic
- [[@chang2020]] — Chang et al. (2019) — Neural lyapunov control
- [[@hakobyan2019]] — Hakobyan et al. (2019) — Risk-Aware Motion Planning and Control Using CVaR-Constrained Optimiza
- [[@lopez2019]] — Lopez et al. (2019) — Dynamic tube MPC for nonlinear systems
- [[@michel2019112]] — Michel et al. (2019) — Design and flight experiments of a Tube-Based Model Predictive Control
- [[@bansal2020]] — Bansal et al. (2020) — DeepReach: A Deep Learning Approach to High-Dimensional Reachability
- [[@fan2020]] — Fan et al. (2020) — Deep Learning Tubes for Tube MPC
- [[@kurtz2020]] — Kurtz et al. (2020) — Robust Approximate Simulation for Hierarchical Control of Linear Syste
- [[@chen2021]] — Chen et al. (2021) — FaSTrack:A Modular Framework for Real-Time Motion Planning and Guarant
- [[@isaacgym]] — Makoviychuk et al. (2021) — Isaac gym: High performance GPU based physics simu-lation for robot le
- [[@rudin2021]] — Rudin et al. (2021) — Learning to Walk in Minutes Using Massively Parallel Deep Reinforcemen
- [[@sieber2021]] — Sieber et al. (2021) — A System Level Approach to Tube-based Model Predictive Control
- [[@zhao2021]] — Zhao et al. (2021) — Tube-Certified Trajectory Tracking for Nonlinear Systems With Robust C
- [[@csomay-s2022]] — Csomay-Shanklin et al. (2022) — Multi-Rate Planning and Control of Uncertain Nonlinear Systems: Model 
- [[@dawson2022safe]] — Dawson et al. (2022) — Safe nonlinear control using robust neural lyapunov-barrier functions
- [[@molnar2022]] — Molnar et al. (2022) — Model-Free Safety-Critical Control for Robotic Systems
- [[@csomay2023]] — Csomay-Shanklin et al. (2023) — Nonlinear Model Predictive Control of a 3D Hopping Robot: Leveraging L
- [[@kaufmann2023]] — Kaufmann et al. (2023) — Champion-level drone racing using deep reinforcement learning
- [[@mathiesen2023]] — Mathiesen et al. (2023) — Safety Certification for Stochastic Systems via Neural Barrier Functio
- [[@pezzato2023samplingbased]] — Pezzato et al. (2023) — Sampling-based model predictive control leveraging parallelizable phys
- [[@salzmann2023neural]] — Salzmann et al. (2023) — Real-time Neural-MPC: Deep Learning Model Predictive Control for Quadr
- [[@wabersich2023data]] — Wabersich et al. (2023) — Data-driven safety filters: Hamilton-jacobi reachability, control barr
- [[@code]] — ? (2024) — Learing Tubes MPC Code
- [[@cohen-2024]] — Cohen et al. (2024) — Safety-critical control for autonomous systems: Control barrier functi
- [[@compton2024]] — Compton et al. (2024) — Constructive Nonlinear Control of Underactuated Systems via Zero Dynam
- [[@cosner2024generative]] — Cosner et al. (2024) — Generative modeling of residuals for real-time risk-sensitive safety w
- [[@csomay2024robust]] — Csomay-Shanklin et al. (2024) — Robust Agility via Learned Zero Dynamics Policies
- [[@do-hal-04620816]] — Do et al. (2024) — Tube MPC via flatness for multicopter trajectory tracking
- [[@li2024]] — Li et al. (2024) — Reinforcement learning for versatile, dynamic, and robust bipedal loco
- [[@liao2024]] — Liao et al. (2024) — Berkeley Humanoid: A Research Platform for Learning-based Control
- [[@salzmann2024l4casadi]] — Salzmann et al. (2024) — Learning for CasADi: Data-driven Models in Numerical Optimization
