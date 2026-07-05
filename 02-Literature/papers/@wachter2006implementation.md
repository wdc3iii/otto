---
type: paper
citekey: wachter2006implementation
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- W\"achter, Andreas
- Biegler, Lorenz T
year: 2006
venue: Mathematical programming
doi: 10.1007/s10107-004-0559-y
arxiv: null
url: https://doi.org/10.1007/s10107-004-0559-y
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- wachter2006implementation
---

# On the implementation of an interior-point filter line-search algorithm for large-scale nonlinear programming

> [!info] W\"achter, Andreas; Biegler, Lorenz T · 2006 · Mathematical programming

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — The reference implementation paper for IPOPT: a primal-dual interior-point method with a filter line-search for large-scale nonlinear programming.
**Problem** — Practical large-scale NLP solvers need globalization and robustness safeguards beyond the bare interior-point iteration, with the theory tied to a concrete, well-engineered implementation.
**Method** — Gives a comprehensive description of the algorithm behind IPOPT: the filter line-search globalization, a feasibility-restoration phase, second-order corrections, and inertia correction of the KKT matrix, plus heuristics for computational speed. (Local/global convergence was established in prior companion work.)
**Key results** — Evaluated on 954 problems from the CUTEr test set, comparing several line-search options and benchmarking against two state-of-the-art interior-point NLP codes.

## Takeaways
- This is the canonical citation for IPOPT — the solver backing most CasADi / OCP / trajectory-optimization pipelines.
- The filter line-search + feasibility-restoration machinery is what makes interior-point NLP robust on hard, infeasible-looking iterates.
- Inertia correction of the KKT matrix is the practical device that keeps steps descent-like on nonconvex problems.

## Relevance to your work
IPOPT is the workhorse NLP backend for the direct-collocation / MPC trajectory optimization common in legged locomotion; [[@terrain2026consistent]] cites it as the solver used for its optimization problems.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `wachter2006implementation`
