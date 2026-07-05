---
type: paper
citekey: mitchell2005time
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Mitchell, Ian M
- Bayen, Alexandre M
- Tomlin, Claire J
year: 2005
venue: IEEE Transactions on automatic control
doi: 10.1109/TAC.2005.851439
arxiv: null
url: https://doi.org/10.1109/TAC.2005.851439
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- mitchell2005time
---

# A time-dependent Hamilton-Jacobi formulation of reachable sets for continuous dynamic games

> [!info] Mitchell, Ian M; Bayen, Alexandre M; Tomlin, Claire J · 2005 · IEEE Transactions on automatic control

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Casts the reachable set of a continuous dynamic game as the zero sublevel set of the viscosity solution to a time-dependent Hamilton-Jacobi-Isaacs PDE, and computes it with level-set methods.
**Problem** — Computing reachable sets for nonlinear systems with inputs and uncertain/adversarial parameters, accurately and without the discontinuous-solution artifacts of earlier formulations.
**Method** — Proves the reachable set equals the zero sublevel set of the viscosity solution of a particular time-dependent HJI PDE. Because that solution is continuous and defined over the whole state space, level-set numerical methods yield more accurate approximations; a numerical toolbox implementation is released.
**Key results** — Correctness verified on a two-vehicle, three-dimensional collision-avoidance example that has a known analytic solution.

## Takeaways
- The canonical HJ-reachability formulation: safety/reach-avoid sets become sublevel sets of a PDE solution, enabling formal guarantees for nonlinear systems with disturbances.
- The differential-game framing naturally handles adversarial inputs and uncertain parameters (worst-case reachability).
- Practically limited by the curse of dimensionality of grid-based PDE solvers — exact for low-dimensional systems.

## Relevance to your work
The reference formulation for worst-case reachable sets and formal safety, the backdrop against which CBF- and predictive-safety approaches like [[@cohen2025safety]] position themselves as more scalable alternatives.

## Concepts


## Source
- Cited by [[@compton2025learning]]
- bibkeys: `mitchell2005time`
