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
[[rl-for-legged-locomotion]] · [[control-lyapunov-function]] · [[massively-parallel-simulation]] · [[reduced-order-model]] · [[control-barrier-function]] · [[hierarchical-control]] · [[motion-imitation]]

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
- [[@li2025clf|CLF-RL]] — CLF-guided RL (external).
- [[@su2025lipm|LIPM-guided RL]] — LIP reference guides a perceptive bipedal policy.
- [[@lee2024integrating]] · [[@bang2024rl]] — model-based footstep planning fused with model-free RL.

**Reference-guided & imitation** — tracking motion priors / trajectories. Concept: [[motion-imitation]].
- [[@liao2025beyondmimic|BeyondMimic]] · [[@wu2026perceptive]] · [[@allshire2025visual]] · [[@liu2025opt2skill|Opt2Skill]] · [[@sleiman2026zest|ZEST]].
- *Generative motion-imitation lineage (character → humanoid; weekly-review 2026-07-26):* [[@peng2018deepmimic|DeepMimic]] → [[@peng2021amp|AMP]] → [[@peng2022ase|ASE]] → [[@luo2023perpetual|PHC]] → [[@luo2024universal|PULSE]] → [[@tessler2024maskedmimic|MaskedMimic]] → [[@wang2026motionbricks|MotionBricks]] (deploys on the G1). The **scale-driven** counterpoint to this map's **structure-driven** through-line — see the tension in [[motion-imitation]].

**Perceptive / terrain-aware locomotion** — conditioning on terrain geometry.
- [[@long2025learning]] · [[@he2025attention]] · [[@zhang2026rpl|RPL]] · [[@zhuang2024humanoid]] · [[@wangndbeamdojo|BeamDojo]] · [[@benndgallant|Gallant]] · [[@jenelten2024dtc|DTC]].

**Sim-to-real dynamic walking**
- [[@yu2022dynamic]] · [[@duan2022sim]].

**Classical ROM stepping (context CLF-RL builds on)** — the reduced models the references come from.
- [[@xiongnd3d|H-LIP]] · [[@xiongndglobal]] — see [[reduced-order-model]].

## Sibling map
[[navigation-autonomy]] (built 2026-07-06) holds the navigation, perception, and safety clusters —
mapless/topological/social nav, traversability, and the PSF safety stack. [[@terrain2026consistent]]
is the hinge between the two maps.
