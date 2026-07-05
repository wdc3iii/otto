---
type: paper
citekey: donald1993kinodynamic
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Donald, Bruce
- Xavier, Patrick
- Canny, John
- Reif, John
year: 1993
venue: Journal of the ACM
doi: https://doi.org/10.1145/174147.174150
arxiv: null
url: https://dl.acm.org/doi/10.1145/174147.174150
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- donald1993kinodynamic
---

# Kinodynamic Motion Planning

> [!info] Donald, Bruce; Xavier, Patrick; Canny, John; Reif, John · 1993 · Journal of the ACM

## Summary
> [!note] AI-drafted from the paper's bibliographic record and abstract — a base to refine.

**TL;DR** — The paper that names and formalizes *kinodynamic* planning: motion planning that must simultaneously satisfy kinematic (obstacle-avoidance) and dynamic (bounded velocity/acceleration/force) constraints, together with provably good approximation algorithms.

**Problem** — Classical motion planning treats geometry and dynamics separately; real robots need trajectories that respect both at once, and the combined problem's complexity/approximability was open.

**Method** — Casts kinodynamic planning as finding a time-optimal, collision-free trajectory subject to dynamics bounds, and gives polynomial-time approximation algorithms (via discretizing the state space and searching) that return trajectories provably close to optimal while respecting the constraints.

**Key results** — Establishes the kinodynamic planning problem and delivers approximation algorithms with provable guarantees on safety and near-optimality.

## Takeaways
- Foundational reference that coined "kinodynamic planning" and framed the joint kinematic-plus-dynamic constraint problem.
- Approximation-algorithm viewpoint: exact time-optimal planning under dynamics is hard, so grid/discretization schemes with provable near-optimality are the tractable route.
- Classical (pre-sampling-based) treatment; complexity grows with state-space dimension, which motivated later randomized planners.

## Relevance to your work
Anchor citation for why locomotion trajectory generation must plan under dynamic feasibility, not just geometry — the motivation behind the dynamically-feasible planning layer in [[@hierarchies2025motion]].

## Concepts


## Source
- Cited by [[@csomayshanklin2025dynamically]], [[@hierarchies2025motion]]
- bibkeys: `donald1993kinodynamic`
