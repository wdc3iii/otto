---
type: moc
tags: [moc, navigation]
aliases: [Navigation autonomy, navigation MOC, humanoid navigation]
created: 2026-07-06
modified: 2026-07-07
---

# Navigation Autonomy

Map of the humanoid **navigation-autonomy** literature and my work in it — anchored on my active
project [[capability-aware-navigation]] and on [[@terrain2026consistent]], the terrain-aware LLC
that is the **hinge** between this map and its sibling [[learning-based-locomotion]]. The stack:
a *frozen* learned locomotion controller, a mid-level nav policy that commands it, and a
geometry/semantics-aware safety filter.

## Concepts
[[mapless-navigation]] · [[topological-navigation]] · [[social-navigation]] · [[traversability-estimation]] · [[recurrent-navigation-policy]] · [[path-conditioned-rl]] · [[capability-awareness]] · [[poisson-safety-function]] · [[control-barrier-function]] · [[sim-to-real-transfer]] · [[hierarchical-control]] · [[control-lyapunov-function]] · [[forward-dynamics-model]] · [[vision-language-action]] · [[foundation-model]]

## The three-tier stack (my project)
1. **Low-level controller (frozen CLF-RL):** [[@li2025clf|CLF-RL]] · [[@olkin2025chasing|Chasing Stability (running)]] · [[@olkin2026chasing|Chasing Autonomy]] · [[@terrain2026consistent|terrain-aware]]. See [[rl-for-legged-locomotion]], [[control-lyapunov-function]], [[hierarchical-control]].
2. **Mid-level navigation policy (mine):** recurrent policy over the frozen LLC → [[capability-aware-navigation]]. Thesis: [[capability-awareness]].
3. **Safety filter (in-group):** [[@bena2025geometry|Poisson Safety Functions → CBF-MPC]] · [[@yang2026safesage|Safe-SAGE (social/semantic)]] → [[poisson-safety-function]], [[social-navigation]].

## The central tension
[[capability-awareness]] argues an analytical ROM can't represent a *learned* controller's feasible-command manifold — the same ROM–reality gap that [[dynamic-tube|DTMPC]] and [[@compton2025learning|predictive CBFs]] answer by *correcting* the ROM. **Correct-the-ROM vs. bypass-it-with $V_t$** is the through-line linking this map to [[learning-based-locomotion]].

> [!note] Open question (weekly-review 2026-07-07, ai-draft) — safety has quietly downgraded from
> *provable* to *empirical* as the work moved ARCHER→G1: the hopper line **proved** RoM→FoM safety
> ([[@cohen2025safety]], [[@compton2025learning]]), whereas the G1 stack wraps a CBF *collision* filter
> around a learned policy with **unbounded tracking error** ([[@terrain2026consistent]], [[@olkin2026chasing]]).
> Recover the guarantee on the learned policy, or consciously accept empirical safety? Full treatment
> in [[capability-awareness]] §Open tensions.

## External lineage, grouped
**ETH/RSL — mapless nav & HRL over a locomotion controller** ([[fan-yang]], [[marco-hutter]])
- [[@yang2025spatially|SRU]] — spatial recurrent memory; my nav-policy architecture anchor.
- [[@lee2024learning]] — wheeled-legged kilometer-scale HRL; my HLC-over-frozen-LLC template.
- [[@hoeller2021learning]] — VAE+LSTM nav predecessor · [[@roth2025learned]] — forward-dynamics + MPPI · [[@haro2026path]] — path-conditioned RL ([[path-conditioned-rl]]).

**Berkeley / Levine — topological navigation** ([[sergey-levine]], [[topological-navigation]])
- [[@shah2023gnm|GNM]] · [[@shah2023vint|ViNT]] · [[@sridhar2024nomad|NoMaD]] — sparse topological maps / foundation models; candidate novelty = capability-annotated edges + campus prior.
  - These are navigation [[foundation-model]]s; NoMaD's action head is a [[diffusion-policy]] on the ViNT [[transformer]] (weekly-review 2026-07-26 link).

**Humanoid nav on the G1**
- [[@zhang2026focusnav|FocusNav]] — the direct contemporary competitor (local nav, G1); distinguish SASG (gates *perception*) from my $V_t$-comfort (penalizes *commands*).
- [[@wang2026guide]] — goal-initialized end-to-end mapless nav (adjacent).
- [[@cheng2024navila|NaVILA]] — legged-robot [[vision-language-action|VLA]] emitting *language* waypoints ("move forward 75cm") to a locomotion RL policy; the VLA instance of high-level-over-frozen-LLC, and a **non-SE(2) interface** data point (cf. [[capability-awareness]] §4/§5).

**Method / architecture**
- [[@wijmans2019ddppo|DD-PPO]] — recurrent-PPO reference · [[@vora2020pointpainting|PointPainting]] — camera→LiDAR semantic fusion.

## People
In-group: [[aaron-ames]] · [[zachary-olkin]] (LLC/$V_t$) · [[ryan-bena]] (safety filter) · [[noel-csomay-shanklin]]. External: [[fan-yang]] · [[marco-hutter]] · [[sergey-levine]].

## Sibling map
[[learning-based-locomotion]] — the locomotion-policy side; [[@terrain2026consistent]] bridges the two.
