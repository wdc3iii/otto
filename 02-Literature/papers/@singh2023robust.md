---
type: paper
citekey: singh2023robust
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Singh, Sumeet
- Landry, Benoit
- Majumdar, Anirudha
- Slotine, Jean-Jacques
- Pavone, Marco
year: 2023
venue: The International Journal of Robotics Research
doi: 10.1177/02783649231186165
arxiv: null
url: https://doi.org/10.1177/02783649231186165
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- SinghIJRR23
- singh2023robust
---

# Robust feedback motion planning via contraction theory

> [!info] Singh, Sumeet; Landry, Benoit; Majumdar, Anirudha; Slotine, Jean-Jacques; Pavone, Marco · 2023 · The International Journal of Robotics Research

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Uses contraction theory (Control Contraction Metrics) to certify a fixed-size tracking tube offline, which an online planner then uses as a robustness margin for collision-free motion planning under disturbances.
**Problem** — Generating motion plans for nonlinear robots that are provably safe (collision-free) under bounded disturbances and control constraints, without being restricted to a precomputed library of maneuvers.
**Method** — Offline, CCMs and convex optimization synthesize a feedback controller structure that tracks any feasible nominal trajectory and characterize a fixed-size invariant tube around it. Online, a motion planner inflates obstacles by the tube and plans nominal trajectories that can be tracked collision-free despite disturbances — unlike funnel-library methods, it is not tied to a fixed maneuver set.
**Key results** — Demonstrated in simulation on planar and 3D quadrotors and in hardware on a quadrotor navigating a cluttered environment under aerodynamic disturbances.

## Takeaways
- Contraction/CCM gives a single fixed tube valid for *any* nominal trajectory, decoupling the (offline) robustness certificate from the (online) planner — more flexible than funnel libraries.
- The tube is fixed-size: robustness is uniform along the trajectory regardless of local maneuver aggressiveness (a limitation that motivates state/input-dependent, dynamic tubes).
- Balances safety and agility, validated on real hardware under real disturbances.

## Relevance to your work
The contraction-theoretic tube-planning baseline your dynamic-tube work builds on and contrasts with — its *fixed* certified tube is precisely the conservatism that [[@compton2025dynamic]] relaxes with state/input-dependent tubes.

## Concepts
[[tracking-error-bound]] · [[tube-mpc]]


## Source
- Cited by [[@cohen2025safety]], [[@compton2025learning]]
- bibkeys: `SinghIJRR23`, `singh2023robust`
