---
type: paper
citekey: borrelli2017predictive
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Borrelli, Francesco
- Bemporad, Alberto
- Morari, Manfred
year: 2017
venue: Higher Education from Cambridge University Press
doi: 10.1017/9781139061759
arxiv: null
url: https://doi.org/10.1017/9781139061759
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- Borrelli
- borrelli2017predictive
- borrelli_predictive_2017
---

# Predictive Control for Linear and Hybrid Systems

> [!info] Borrelli, Francesco; Bemporad, Alberto; Morari, Manfred · 2017 · Higher Education from Cambridge University Press

## Summary
> [!note] AI-drafted from the publisher abstract — a base to refine.
**TL;DR** — The definitive graduate textbook on model predictive control for linear and hybrid systems, with heavy emphasis on explicit MPC and real-time implementation.
**Problem** — Provides a unified, rigorous treatment of MPC theory — stability, feasibility, and robustness — that also transfers to practice.
**Method** — Builds MPC from multiparametric programming: for linear systems with linear constraints (and switched/linear hybrid systems), it derives *explicit* MPC where the optimal feedback law is a precomputed piecewise-affine map of the state, avoiding online optimization. Covers design of predictive control laws with numerous worked examples and applications.
**Key results** — Comprehensive reference-grade coverage of constrained optimal control, invariant sets, multiparametric/explicit MPC, and hybrid-system MPC; a textbook, not a single result.

## Takeaways
- Canonical source for MPC stability/feasibility/invariant-set theory and for explicit (multiparametric) MPC.
- Hybrid-systems MPC coverage makes it the standard reference when discrete modes/contacts enter the optimal-control formulation.
- Cited for foundational definitions and guarantees rather than a specific novel algorithm.

## Relevance to your work
This is the standard reference for the constrained-optimal-control and robust-MPC machinery underpinning tube- and hierarchical-MPC schemes; [[@csomayshanklin2024robust]] and the hierarchical/contract-theory work cite it as the MPC foundation.



## Abstract (from bib)
Model Predictive Control (MPC), the dominant advanced control approach in industry over the past twenty-five years, is presented comprehensively in this unique book. With a simple, unified approach, and with attention to real-time implementation, it covers predictive control theory including the stability, feasibility, and robustness of MPC controllers. The theory of explicit MPC, where the nonlinear optimal feedback controller can be calculated efficiently, is presented in the context of linear systems with linear constraints, switched linear systems, and, more generally, linear hybrid systems. Drawing upon years of practical experience and using numerous examples and illustrative applications, the authors discuss the techniques required to design predictive control laws, including algori

## Concepts

## Source
- Cited by [[@contract2025theory]], [[@csomayshanklin2024robust]], [[@hierarchies2025motion]]
- bibkeys: `Borrelli`, `borrelli2017predictive`, `borrelli_predictive_2017`
- DOI: https://doi.org/10.1017/9781139061759
