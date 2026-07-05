---
type: paper
citekey: gill2005snopt
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Gill, Philip E
- Murray, Walter
- Saunders, Michael A
year: 2005
venue: SIAM review
doi: 10.1137/S0036144504446096
arxiv: null
url: https://doi.org/10.1137/S0036144504446096
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@gill2005snopt.pdf
bibkeys:
- gill2005snopt
---

# SNOPT: An SQP algorithm for large-scale constrained optimization

> [!info] Gill, Philip E; Murray, Walter; Saunders, Michael A · 2005 · SIAM review

## Summary
> [!note] AI-drafted from the abstract — a base to refine.

**TL;DR** — SNOPT is a sequential quadratic programming (SQP) solver for large-scale smooth nonlinear constrained optimization, built around a limited-memory quasi-Newton Hessian and a sparse reduced-Hessian QP subproblem solver.

**Problem** — Efficiently solving smooth nonlinear programs with general (linear and nonlinear) inequality constraints, where first derivatives are available and constraint gradients are sparse.

**Method** — An SQP algorithm using a smooth augmented-Lagrangian merit function with explicit provision for infeasibility in both the original problem and the QP subproblems. SNOPT uses a limited-memory quasi-Newton approximation to the Lagrangian Hessian and a reduced-Hessian QP solver (SQOPT) for the subproblems, targeting problems with many thousands of variables/constraints but a moderate number of degrees of freedom (up to ~2000).

**Key results** — Numerical results reported on most problems in the CUTE test set (abstract truncated on the fetched source).

## Takeaways
- Standard workhorse NLP solver for trajectory optimization and optimal control; favors problems with few degrees of freedom relative to total variables.
- Limited-memory quasi-Newton + reduced-Hessian design keeps it viable at large scale when the Hessian is not formed explicitly.
- Requires only first derivatives and exploits sparse constraint Jacobians.

## Relevance to your work
The SQP/NLP backend commonly used to solve MPC and trajectory-optimization problems; cited as the numerical solver underlying such formulations. See [[@compton2025dynamic]].

## Concepts


## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `gill2005snopt`
