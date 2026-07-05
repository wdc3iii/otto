---
type: paper
citekey: andersson2019casadi
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Joel A E Andersson
- Joris Gillis
- Greg Horn
- James B Rawlings
- Moritz Diehl
year: 2019
venue: Mathematical Programming Computation
doi: 10.1007/s12532-018-0139-4
arxiv: null
url: https://doi.org/10.1007/s12532-018-0139-4
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- Andersson2019
---

# CasADi -- A software framework for nonlinear optimization and optimal control

> [!info] Joel A E Andersson; Joris Gillis; Greg Horn; James B Rawlings; Moritz Diehl · 2019 · Mathematical Programming Computation

## Summary
> [!note] AI-drafted from the paper's title/canonical description (publisher abstract unavailable) — a base to refine.
**TL;DR** — CasADi is an open-source software framework that makes it easy to formulate and solve nonlinear optimization and optimal-control problems, built around efficient symbolic expressions and algorithmic (automatic) differentiation.
**Problem** — Implementing gradient/Jacobian/Hessian-based methods for optimal control and dynamic optimization by hand is error-prone and time-consuming; practitioners need a general, efficient tool to build these problems and hand them to numerical solvers.
**Method** — CasADi provides a symbolic expression graph with sparsity-aware algorithmic differentiation (forward and reverse modes) and interfaces to numerical routines — NLP solvers (e.g., IPOPT), QP solvers, and ODE/DAE integrators with sensitivity analysis — so users assemble discretization schemes (direct collocation, multiple shooting) in a host language (Python/MATLAB/C++).
**Key results** — This paper is the reference description of the framework's design and capabilities; it has become a de-facto standard tool for prototyping MPC, trajectory optimization, and optimal-control formulations.

## Takeaways
- The value proposition is the combination of *symbolic modeling* + *automatic differentiation* + *solver interfaces* in one open-source package, not a new algorithm.
- It is infrastructure: it computes exact derivatives efficiently but relies on external solvers (IPOPT, qpOASES, etc.) for the actual optimization.
- Because it is a tooling citation rather than a method, papers cite it to state *how* their optimal-control/MPC problems were implemented.

## Relevance to your work
This is almost certainly cited as the implementation backbone for the MPC / trajectory-optimization solves in [[@compton2025dynamic]] and terrain2026consistent — the standard toolchain for turning a control formulation into a differentiable NLP.

## Concepts


## Source
- Cited by [[@compton2025dynamic]], [[@terrain2026consistent]]
- bibkeys: `Andersson2019`
- DOI: https://doi.org/10.1007/s12532-018-0139-4
