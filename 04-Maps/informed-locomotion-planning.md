---
type: moc
tags: [moc, planning, control]
aliases: [Informed locomotion planning, Planning under model mismatch, Naive vs informed planning]
created: 2026-07-06
modified: 2026-07-07
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
[[tube-mpc]] · [[dynamic-tube]] · [[tracking-error-bound]] · [[forward-dynamics-model]] · [[sampling-based-optimization]] · [[reduced-order-model]] · [[capability-awareness]] · [[traversability-estimation]] · [[hierarchical-control]]

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

### Robust learned tracker (absorb the gap, don't bound it)
A third answer to model mismatch the imported taxonomy lacked: don't *bound* the gap (tube) or
*predict* it (FDM) — **train a tracker robust enough that the residual gap doesn't matter**, and let
a foresighted planner / safety-filter ride on top. This is where my *current* G1 line actually sits.
- [[@jenelten2024dtc|DTC]] — MPC supplies foresight while an RL layer compensates for model mismatch; the canonical "optimizer + robust learned tracker" split.
- [[@terrain2026consistent|Terrain-Consistent RL (mine)]] — an RL policy tracks terrain-consistent references under a CBF-MPC planner: a learned tracker + safety-filter planner, *not* a tube.
- [[@olkin2026chasing|Chasing Autonomy]] — RL runner under a PSF→CBF-MPC safety filter over a frozen controller; same pattern.

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

> [!note] Reframing (weekly-review 2026-07-07, ai-draft) — the "certified vs. learned-soft" split
> above is overdrawn. My own [[@compton2025dynamic|DTMPC]] tube is an **α = 0.9 quantile** bound —
> *learned and statistical, with no hard guarantee* — so it sits **with** the FDM family, not
> opposite it. The honest axis is **what is bounded**: DTMPC bounds *tracking error around a
> reference* (structured); the FDM bounds *task failure / achievable pose* (end-to-end); the
> robust-tracker route *absorbs* the gap. The genuinely **certified** members belong in their own
> row: [[@cohen2025safety|simulation-function safety]], [[@compton2025learning|predictive-robustness CBFs]]
> ("we *prove* this guarantees safety"), and [[@herbert2017fastrack|FaSTrack]] (reachability bound).
> And note the trajectory of my own work: it **migrated from bound-the-gap (ARCHER / DTMPC) to
> learn-a-robust-tracker (G1)** — this map's original framing filed my current work as "tube" when
> it's really the robust-tracker family above. Related open question in [[capability-awareness]].

## Sibling maps
- [[learning-based-locomotion]] — the prior taxonomy's *LeggedLocomotion* tree (RoM / MPC / RL).
- [[navigation-autonomy]] — the prior taxonomy's *LocomotionAutonomy* tree (SLAM / high-level planning); [[@terrain2026consistent]] hinges the stack.

## Concepts created from this ingestion
These atomic notes were drafted to hold the ideas the ingestion surfaced (all `ai-draft`, `to-revisit` — refine into your own words):
- [[forward-dynamics-model]] — learned predictor of achievable motion + failure risk; the FDM node from the old taxonomy, central to my humanoid project. Grounds [[@roth2025learned]], [[@kim2022forward]], [[@gibson2023multi]], [[@lee2023terrain]], [[@pokhrel2024cahsor]], [[@beyer2024risk]].
- [[step-to-step-dynamics]] — discrete foot-placement→next-step map (H-LIP) for underactuated bipedal walking; specialized [[reduced-order-model]]. Grounds [[@xiong2019orbit]], [[@xiongnd3d]], [[@xiongndglobal]], [[@dai2021bipedal]], [[@dai2023data]].
- [[contact-implicit-mpc]] — whole-body NMPC with contact timing/location optimized, not prespecified; the opposite end of my MPC spectrum from tube/ROM. Grounds [[@neunert2018whole]].
- [[sampling-based-optimization]] — sampling planners (MPPI) paired with learned models/costs; recurs across the FDM family and [[@tracy2025trajectory]].
- [[state-estimation]] — the LiDAR-inertial odometry / localization layer feeding perceptive planning; grounds [[@nubert2025holistic]], [[@quenzel2025lio]].
