---
type: moc
tags: [moc, rl, locomotion]
aliases: [Learning-based locomotion, RL locomotion MOC, learned locomotion map]
created: 2026-07-06
modified: 2026-07-06
---

# Learning-based Locomotion

Map of the learning-for-legged-locomotion literature as it bears on my work — anchored on the
CLF-guided RL line and the navigation-autonomy paper [[@terrain2026consistent]], whose citation
list this map organizes. The through-line: **inject structure (reduced-order models, control
Lyapunov functions, references) into RL** rather than hand-tuning rewards — for precise,
certifiable, planner-compatible locomotion.

## Concepts
[[rl-for-legged-locomotion]] · [[control-lyapunov-function]] · [[massively-parallel-simulation]] · [[reduced-order-model]] · [[control-barrier-function]] · [[hierarchical-control]]

## My contributions (CLF-guided RL line)
- [[@dai2025walk|PLANC]] — ROM stepping planner + CLF rewards for constrained footholds.
- [[@olkin2026stability]] — stability theory of CLF-guided RL.
- [[@olkin2026chasing]] — dynamic retargeting + control-guided RL for controllable running.
- [[@terrain2026consistent]] — terrain-consistent references + CLF-RL exposing an $SE(2)$ navigation interface.

## The literature, grouped

**Foundations & training infrastructure** — the model-free-RL-at-scale recipe.
- [[@hwangbo2019learning]] — the foundational agile RL locomotion result (ANYmal).
- [[@mittal2025isaac|Isaac Lab]] · [[@schwarke2025rsl|RSL-RL]] — the GPU sim + RL library the pipeline runs on ([[massively-parallel-simulation]]).

**Structure-guided RL** — ROM / CLF guidance instead of pure reward shaping.
- [[@li2025clf|CLF-RL]] — CLF-guided RL (external; note: also keyed `@li2026clf` — duplicate to merge).
- [[@su2025lipm|LIPM-guided RL]] — LIP reference guides a perceptive bipedal policy.
- [[@lee2024integrating]] · [[@bang2024rl]] — model-based footstep planning fused with model-free RL.

**Reference-guided & imitation** — tracking motion priors / trajectories.
- [[@liao2025beyondmimic|BeyondMimic]] · [[@wu2026perceptive]] · [[@allshire2025visual]] · [[@liu2025opt2skill|Opt2Skill]] · [[@sleiman2026zest|ZEST]].

**Perceptive / terrain-aware locomotion** — conditioning on terrain geometry.
- [[@long2025learning]] · [[@he2025attention]] · [[@zhang2026rpl|RPL]] · [[@zhuang2024humanoid]] · [[@wangndbeamdojo|BeamDojo]] · [[@benndgallant|Gallant]] · [[@jenelten2024dtc|DTC]].

**Sim-to-real dynamic walking**
- [[@yu2022dynamic]] · [[@duan2022sim]].

**Classical ROM stepping (context CLF-RL builds on)** — the reduced models the references come from.
- [[@xiongnd3d|H-LIP]] · [[@xiongndglobal]] — see [[reduced-order-model]].

## Adjacent maps (to build)
The terrain paper also cites a **navigation-autonomy** stack (LiDAR-inertial odometry, traversability,
planning: `@xu2021fast`, `@xu2022fast`, `@compton2026lio`, `@dixit2024step`, `@lin2021long`,
`@lee2024asap`, `@cheng2024navila`, `@yoon2025state`) — those belong in a future
`navigation-autonomy` MOC, not here. See the full list in [[@terrain2026consistent]].
