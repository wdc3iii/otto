---
type: moc
tags: [moc, planning, control]
aliases: [Informed locomotion planning, Planning under model mismatch, Naive vs informed planning]
created: 2026-07-06
modified: 2026-07-06
---

# Informed Locomotion Planning (planning under model mismatch)

Map of the "does the planner account for the gap between its model and what the robot
actually does?" literature — the organizing axis of my prior literature vault's
**LocomotionPlanning** tree, now folded into otto. The through-line and my own contribution
([[@compton2024dynamic|Dynamic Tube MPC]]) live on the same question: a plan is generated on
a *reduced* model, but execution happens on the *full* system; **informed** planning carries
an explicit model of that mismatch — as a tube, an error bound, or a learned forward-dynamics /
risk model — instead of assuming the plan is tracked perfectly.

> [!note] Imported taxonomy. This MOC preserves the structure of the retired `literature-vault`
> (Naive → Informed → {Tube, FDM}). Its sibling trees map to the existing [[learning-based-locomotion]]
> and [[navigation-autonomy]] MOCs (see *Sibling maps* below).

## Concepts
[[tube-mpc]] · [[dynamic-tube]] · [[tracking-error-bound]] · [[reduced-order-model]] · [[capability-awareness]] · [[traversability-estimation]] · [[hierarchical-control]]

## The axis

**Naive planning** — plan on a model, track open-loop, hope the mismatch is small. The baseline
the rest of this map reacts against; adequate only when the tracking controller's error is
negligible relative to the safety margin.

**Informed planning** — the plan carries an explicit representation of model mismatch. Two
families:

### Tube-based (certificate / bound on the tracking error)
The reduced-order plan is wrapped in a **tube** the full system is guaranteed (or learned) to
stay within; the planner then reasons over the inflated geometry.
- [[@lopez2019dynamic|Dynamic Tube MPC]] — the reference formulation: co-design plan + tube online.
- [[@compton2024dynamic|Dynamic Tube MPC (mine)]] — **learn** the tube dynamics with massively-parallel sim for robust safety in practice.
- [[@fan2020deep|Deep Learning Tubes]] — learned tube geometry from data.
- [[@herbert2017fastrack|FaSTrack]] · [[@fridovichkeil2018planning|Planning Fast & Slow]] — precomputed tracking-error bound via reachability; a fast planner inside a slow safety envelope. See [[tracking-error-bound]].
- [[@tracy2025trajectory|Trajectory Bundle Method]] — derivative-free SCP over sampled rollouts; adjacent tooling for optimizing under sampled dynamics.

### Forward-dynamics-model based (learned predictor of achievable motion + risk)
Instead of a certified bound, **learn** what the platform will actually do (and where it fails),
then plan against that predictor. This is the family my humanoid FDM project sits in — see the
extension notes in [[@roth2025learned]].
- [[@roth2025learned|Learned Perceptive FDM]] — predicts future SE(2) pose **and** failure risk; planner (MPPI) optimizes commands subject to a risk threshold. The closest prior art to my line.
- [[@kim2022forward|Learning Forward Dynamics]] · [[@gibson2023multi|Multi-step Dynamics]] — learned (multi-step) dynamics feeding trajectory selection.
- [[@lee2023terrain|Terrain-aware kinodynamic model]] — learned terrain-conditioned dynamics for off-road planning.
- [[@pokhrel2024cahsor|CAHSOR]] — competence-aware high-speed off-road; a learned model that respects the platform's limits ([[capability-awareness]]).
- [[@beyer2024risk|Risk-Predictive Planning]] — learned riskmaps for off-road autonomy.
- [[@meng2023terrainnet|TerrainNet]] · [[@patel2024roadrunner|RoadRunner M&M]] — learned terrain/traversability models the planner consumes ([[traversability-estimation]]).

### Abstraction / uncertainty-aware planning
- [[@jiang2023abstraction|Abstraction-Based Planning]] — uncertainty-aware legged planning over an abstracted model.
- [[@wang2024history|History-Aware Planning]] — memory across visits to reduce risk; resonates with extension (2) in my [[@roth2025learned]] notes.

## Contradiction / tension to chew on
The two informed families answer the same question differently, and it's worth resolving for the
G1: the **tube/FaSTrack** route gives a *certified* bound (trustworthy, conservative, needs a model
you can bound), while the **FDM** route gives a *learned soft risk* (captures un-modeled slip/soft
terrain, but only as good as its training distribution and has no guarantee). My [[@roth2025learned]]
notes frame exactly this — should capability-awareness be a **hard forward-invariance constraint**
(CBF/tube) or a **learned cost** (FDM risk head)? This MOC is where that argument should mature.

## Sibling maps
- [[learning-based-locomotion]] — the prior taxonomy's *LeggedLocomotion* tree (RoM / MPC / RL).
- [[navigation-autonomy]] — the prior taxonomy's *LocomotionAutonomy* tree (SLAM / high-level planning); [[@terrain2026consistent]] hinges the stack.

## Proposed new concepts (surfaced during ingestion — not yet created)
Flagged for your approval rather than added silently (otto grows its concept set deliberately):
- **forward-dynamics-model** — learned predictor of achievable motion + failure risk; the FDM node from the old taxonomy, central to my humanoid project. Grounds [[@roth2025learned]], [[@kim2022forward]], [[@gibson2023multi]], [[@lee2023terrain]], [[@pokhrel2024cahsor]].
- **step-to-step-dynamics / H-LIP** — discrete foot-placement→next-step map for underactuated bipedal walking; currently folded under [[reduced-order-model]]. Grounds [[@xiong2019orbit]], [[@dai2021bipedal]], [[@dai2023data]].
- **contact-implicit-mpc** — whole-body NMPC with contact timing/location optimized, not prespecified; the opposite end of my MPC spectrum from tube/ROM. Grounds [[@neunert2018whole]].
- **sampling-based-optimization (MPPI)** — sampling planners paired with learned models/costs; recurs across the FDM family and [[@tracy2025trajectory]].
- **state-estimation / LiDAR-inertial odometry** — the estimation layer feeding perceptive planning; grounds [[@nubert2025holistic]], [[@quenzel2025lio]].
