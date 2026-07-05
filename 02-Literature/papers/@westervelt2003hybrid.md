---
type: paper
citekey: westervelt2003hybrid
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Westervelt, E.R.
- Grizzle, J.W.
- Koditschek, D.E.
year: 2003
venue: IEEE Transactions on Automatic Control
doi: 10.1109/TAC.2002.806653
arxiv: null
url: https://doi.org/10.1109/TAC.2002.806653
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- westervelt2003hybrid
- westervelt_hybrid_2003
---

# Hybrid zero dynamics of planar biped walkers

> [!info] Westervelt, E.R.; Grizzle, J.W.; Koditschek, D.E. · 2003 · IEEE Transactions on Automatic Control

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces hybrid zero dynamics (HZD): a constructive method for designing provably, exponentially stable walking controllers for planar underactuated bipeds.
**Problem** — Underactuated bipeds (one more DOF than actuators) are hybrid systems whose periodic gaits are hard to stabilize with formal guarantees.
**Method** — Virtual-constraint output functions drive the system to an attracting 2D zero-dynamics submanifold of the full hybrid model, whose restriction dynamics reduce to a scalar linear time-invariant Poincaré return map. Exponentially stable orbits of this low-dimensional zero dynamics correspond to exponentially stabilizable orbits of the full model; parameter optimization tunes the HZD for low-energy walking under kinematic/dynamic constraints.
**Key results** — General theory proven for planar bipeds and illustrated on a five-link walker (torso + two legs with knees), yielding stable low-energy gaits.

## Takeaways
- HZD collapses a high-DOF hybrid walking problem to a scalar return map — the enabling idea for constructive, certifiable gait design.
- Virtual constraints (output functions) are the design knob; stability of the reduced zero dynamics implies stability of the full system.
- Underactuation is handled directly rather than avoided — a key distinction from fully-actuated ZMP approaches.

## Relevance to your work
Foundational reference for reduced-order, formally-stable gait design that model-based planning and CLF/HZD-guided RL for legged systems build on. See [[@hierarchies2025motion]].

## Abstract (from bib)
Planar, underactuated, biped walkers form an important domain of applications for hybrid dynamical systems. This paper presents the design of exponentially stable walking controllers for general planar bipedal systems that have one degree-of-freedom greater than the number of available actuators. The within-step control action creates an attracting invariant set - a two-dimensional zero dynamics submanifold of the full hybrid model \$whose restriction dynamics admits a scalar linear time-invariant return map. Exponentially stable periodic orbits of the zero dynamics correspond to exponentially stabilizable orbits of the full model. A convenient parameterization of the hybrid zero dynamics is imposed through the choice of a class of output functions. Parameter optimization is used to tune t

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@compton2024constructive]], [[@csomayshanklin2024robust]], [[@hierarchies2025motion]], [[@olkin2026stability]]
- bibkeys: `westervelt2003hybrid`, `westervelt_hybrid_2003`
- DOI: https://doi.org/10.1109/TAC.2002.806653
