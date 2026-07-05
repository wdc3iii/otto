---
type: paper
citekey: diehl2005real
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Diehl, Moritz
- Bock, Hans Georg
- Schl\"oder, Johannes P
year: 2005
venue: SIAM Journal on control and optimization
doi: 10.1137/S0363012902400713
arxiv: null
url: https://doi.org/10.1137/S0363012902400713
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- diehl2005real
---

# A real-time iteration scheme for nonlinear optimization in optimal feedback control

> [!info] Diehl, Moritz; Bock, Hans Georg; Schl\"oder, Johannes P · 2005 · SIAM Journal on control and optimization

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Presents and analyzes an efficient Newton-type real-time iteration scheme for approximate online solution of the optimization problems arising in optimal feedback control, with a proof of contractivity and a bound on suboptimality.
**Problem** — Optimal feedback control requires solving an optimization problem online fast enough to react to disturbances, which exact solution cannot meet in real time.
**Method** — The scheme delivers approximations of the exact optimal feedback that are iteratively refined during the runtime of the controlled process, reacting quickly to disturbances. The authors prove contractivity of the real-time iteration and derive a bound on the loss of optimality relative to the theoretical optimal solution.
**Key results** — Robustness and real-time performance demonstrated on an unstable system — control of an airborne kite flying loops.

## Takeaways
- Provides the theoretical backbone (contractivity + suboptimality bound) for the real-time iteration NMPC approach.
- Approximate-but-refined feedback enables fast disturbance rejection without solving the full OCP each step.
- Companion in spirit to the Diehl et al. large-scale NMPC method papers.

## Relevance to your work
The convergence and suboptimality guarantees here justify using single-iteration NMPC solvers online, relevant background for the real-time MPC in your dynamic-tube planning such as [[@compton2025dynamic]].

## Concepts


## Source
- Cited by [[@compton2025learning]]
- bibkeys: `diehl2005real`
