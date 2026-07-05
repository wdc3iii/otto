---
type: paper
citekey: webb2013kinodynamic
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Webb, Dustin J.
- van den Berg, Jur
year: 2013
venue: 2013 IEEE International Conference on Robotics and Automation
doi: 10.1109/ICRA.2013.6631299
arxiv: '1205.5088'
url: https://arxiv.org/abs/1205.5088
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@webb2013kinodynamic.pdf
bibkeys:
- webb_kinodynamic_2013
---

# Kinodynamic RRT*: Asymptotically optimal motion planning for robots with linear dynamics

> [!info] Webb, Dustin J.; van den Berg, Jur · 2013 · 2013 IEEE International Conference on Robotics and Automation

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Kinodynamic RRT* extends RRT* to systems with (controllable) linear dynamics using an optimal fixed-final-state, free-final-time steering controller, yielding asymptotically optimal motion plans that respect differential constraints.
**Problem** — RRT* was posed for holonomic robots; extending asymptotic optimality to kinodynamic systems requires an exact optimal "connect" (steering) primitive between arbitrary state pairs under the dynamics.
**Method** — A fixed-final-state-free-final-time LQR-style controller optimally connects any two states, with cost trading off trajectory duration against control effort; this primitive drives RRT*'s rewiring. The result guarantees asymptotic optimality for any controllable linear system in any state-space dimension, and applies to nonlinear dynamics via first-order Taylor approximation.
**Key results** — For the subclass with nilpotent dynamics matrices, closed-form optimal trajectories are derived (keeping overhead near vanilla RRT*); demonstrated on a planar double integrator, a linearized quadrotor, and a car-like robot.

## Takeaways
- The enabling piece is an exact optimal two-point boundary-value steering solution, not the tree search itself — that is what buys asymptotic optimality under kinodynamic constraints.
- Closed-form solutions for nilpotent systems keep it computationally competitive with holonomic RRT*.
- Optimality guarantee is exact only for controllable *linear* dynamics; nonlinear systems are handled through local linearization.

## Relevance to your work
A canonical sampling-based kinodynamic planner that layered planning/control stacks build on to generate dynamically feasible reference trajectories, e.g. as the planning layer feeding a tracking controller in [[@hierarchies2025motion]].

## Abstract (from bib)
We present Kinodynamic RRT*, an incremental sampling-based approach for asymptotically optimal motion planning for robots with linear dynamics. Our approach extends RRT*, which was introduced for holonomic robots [10], by using a ﬁxed-ﬁnal-state-free-ﬁnal-time controller that optimally connects any pair of states, where the cost function is expressed as a trade-off between the duration of a trajectory and the expended control effort. Our approach generalizes earlier work on RRT* for kinodynamic systems, as it guarantees asymptotic optimality for any system with controllable linear dynamics, in state spaces of any dimension. In addition, we show that for the rich subclass of systems with a nilpotent dynamics matrix, closed-form solutions for optimal trajectories can be derived, which keeps 

## Concepts


## Source
- Cited by [[@csomayshanklin2025dynamically]], [[@hierarchies2025motion]]
- bibkeys: `webb_kinodynamic_2013`
- DOI: https://doi.org/10.1109/ICRA.2013.6631299
