---
type: paper
citekey: rawlings2017model
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Rawlings, J.B.
- Mayne, D.Q.
- Diehl, M.
year: 2017
venue: Nob Hill Publishing
doi: null
arxiv: null
url: https://books.google.com/books?id=MrJctAEACAAJ
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- mpc_book
---

# Model Predictive Control: Theory, Computation, and Design

> [!info] Rawlings, J.B.; Mayne, D.Q.; Diehl, M. · 2017 · Nob Hill Publishing

## Summary
> [!note] AI-drafted from the known scope of this textbook (no abstract available) — a base to refine.
**TL;DR** — The canonical graduate textbook on model predictive control, covering the theory (stability, feasibility, robustness), computation (numerical optimization for MPC), and design of MPC for constrained systems.
**Problem** — MPC needs a unified, rigorous treatment tying together receding-horizon optimal control, its stability and recursive-feasibility guarantees, state estimation, and the numerical methods that make it implementable.
**Method** — A textbook synthesis: it develops deterministic and stochastic/robust MPC, terminal-cost/terminal-set constructions for closed-loop stability and recursive feasibility, moving-horizon estimation as the dual of MPC, distributed MPC, and the numerical optimization (including sensitivity/real-time methods, reflecting Diehl's contributions) used to solve the underlying optimal-control problems.
**Key results** — Not an empirical paper; the enduring contributions are the stability/feasibility theory for constrained receding-horizon control and the treatment of robust MPC (including tube-based approaches) as standard reference material.

## Takeaways
- The standard reference cited to ground MPC stability, recursive feasibility, and terminal-ingredient design.
- Covers robust/tube MPC and moving-horizon estimation, not just nominal MPC — the parts most relevant to real robots facing disturbance and model error.
- As a textbook it is a foundational citation, not a novel method; useful for pinning down definitions and guarantees precisely.

## Relevance to your work
The foundational MPC reference behind any receding-horizon controller in a locomotion stack; a dynamic-planning paper like [[@csomayshanklin2025dynamically]] cites it for the stability/feasibility theory and the robust (tube) MPC machinery that underpin real-time locomotion controllers.

## Concepts
[[tube-mpc]]

## Source
- Cited by [[@csomayshanklin2025dynamically]]
- bibkeys: `mpc_book`
- URL: https://books.google.com/books?id=MrJctAEACAAJ
