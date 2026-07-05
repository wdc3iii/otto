---
type: paper
citekey: stellato2020osqp
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Bartolomeo Stellato
- Goran Banjac
- Paul Goulart
- Alberto Bemporad
- Stephen Boyd
year: 2020
venue: Mathematical Programming Computation
doi: 10.1007/s12532-020-00179-2
arxiv: '1711.08013'
url: https://doi.org/10.1007/s12532-020-00179-2
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@stellato2020osqp.pdf
bibkeys:
- osqp
---

# OSQP: An Operator Splitting Solver for Quadratic Programs

> [!info] Bartolomeo Stellato; Goran Banjac; Paul Goulart; Alberto Bemporad; Stephen Boyd · 2020 · Mathematical Programming Computation

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — OSQP is a robust, general-purpose ADMM-based solver for convex quadratic programs, engineered for embedded and real-time use via factorization caching and warm starting.

**Problem** — Real-time and embedded QP (e.g. MPC, control QPs) need a solver that is fast on parametrized problems, imposes no strong assumptions on the data, and can reliably detect infeasibility — properties interior-point methods do not fully provide.

**Method** — An operator-splitting (ADMM) method whose novelty is that each iteration solves a quasi-definite linear system with the *same* coefficient matrix, so a single initial factorization can be cached and reused; after factorization the algorithm can run division-free. It requires no positive-definiteness of the objective or independence of constraints and is the first splitting method for QPs to reliably detect primal/dual infeasibility from the iterates.

**Key results** — The open-source C implementation is small, library-free, and warm-startable; the authors report it is typically ~10x faster than interior-point solvers (and much more with caching/warm starts), with wide adoption across control, finance, and ML.

## Takeaways
- Same-matrix ADMM iterations make factorization caching + warm starting the killer feature for parametrized/real-time QPs.
- No data assumptions (indefinite objectives, dependent constraints OK) and reliable infeasibility detection — practical robustness over raw speed.
- Numbers (~10x vs interior-point) are the authors' own benchmarks, not universal guarantees.

## Relevance to your work
OSQP is a standard workhorse for solving the QPs at the fast layer of a control stack — MPC, CLF-QP, and CBF-QP safety filters — where warm-started, embeddable solves matter; hence its use in the dynamically-feasible planning of [[@csomayshanklin2025dynamically]].

## Concepts


## Source
- Cited by [[@csomayshanklin2025dynamically]], [[@hierarchies2025motion]]
- bibkeys: `osqp`
- DOI: https://doi.org/10.1007/s12532-020-00179-2
