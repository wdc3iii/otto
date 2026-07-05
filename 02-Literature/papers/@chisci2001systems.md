---
type: paper
citekey: chisci2001systems
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- L. Chisci
- J.A. Rossiter
- G. Zappa
year: 2001
venue: Automatica
doi: https://doi.org/10.1016/S0005-1098(01)00051-6
arxiv: null
url: https://doi.org/10.1016/S0005-1098(01)00051-6
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- shrinking_tube
---

# Systems with persistent disturbances: predictive control with restricted constraints

> [!info] L. Chisci; J.A. Rossiter; G. Zappa · 2001 · Automatica

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A robust predictive-control scheme for constrained linear systems with persistent bounded disturbances that enforces robustness by tightening (restricting) the constraints along the prediction horizon.
**Problem** — The joint presence of hard state/input constraints and persistent disturbances can drive a predictive controller into infeasibility and instability.
**Method** — Suitable constraint restrictions are inserted into the predictive controller so that, for all admissible disturbances, feasibility is preserved; the resulting controller guarantees constraint satisfaction and asymptotic regulation whenever the initial state is feasible.
**Key results** — Proves convergence of the state to a minimal robust invariant set under all admissible disturbances, with simulations demonstrating effectiveness.

## Takeaways
- One of the foundational constraint-tightening ("shrinking/restricted constraint") robust-MPC constructions — the discrete-time backbone of tube MPC.
- Robustness is bought by shrinking the constraint set inward along the horizon so disturbance excursions stay admissible; convergence is to a robust invariant set, not a point.
- Scope is constrained linear discrete-time systems with bounded disturbances.

## Abstract (from bib)
This paper addresses predictive state regulation of linear discrete-time systems subject to persistent bounded disturbances and to state and/or control constraints. It is well known that the joint presence of constraints and disturbances can drive a predictive controller to infeasibility and instability. Here it is shown how robustness against persistent bounded disturbances can be enforced by inserting in the predictive controller suitable constraint restrictions. The robust predictive controller obtained in this way guarantees, for all admissible disturbances, constraint fulfillment and asymptotic state regulation, i.e. convergence of the state to a minimal robust invariant set, provided that the initial state is feasible. Simulation results demonstrate the effectiveness of the proposed 

## Relevance to your work
The `shrinking_tube` bibkey is apt: this is the constraint-tightening precursor to tube MPC, directly relevant to the robust tracking-tube guarantees you build in [[@csomayshanklin2024robust]].

## Concepts
[[tube-mpc]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `shrinking_tube`
- DOI: https://doi.org/https://doi.org/10.1016/S0005-1098(01)00051-6
