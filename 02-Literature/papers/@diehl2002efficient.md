---
type: paper
citekey: diehl2002efficient
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Diehl, Moritz
- Findeisen, Rolf
- Schwarzkopf, Stefan
- Uslu, Ilknur
- Allg\"ower, Frank
- Bock, Hans Georg
- Gilles, Ernst-Dieter
- Schl\"oder, Johannes P
year: 2002
venue: Automation technology
doi: 10.1524/auto.2002.50.12.557
arxiv: null
url: https://doi.org/10.1524/auto.2002.50.12.557
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- diehl2002efficient
---

# An efficient algorithm for nonlinear model predictive control of large-scale systems part I

> [!info] Diehl, Moritz; Findeisen, Rolf; Schwarzkopf, Stefan; Uslu, Ilknur; Allg\"ower, Frank; Bock, Hans Georg · 2002 · Automation technology

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces the *real-time iteration scheme*, an efficient online-optimization algorithm for nonlinear MPC of large-scale systems (Part I: method description).
**Problem** — Solving a full nonlinear optimal control problem every sampling instant is intractable for large-scale NMPC.
**Method** — Built on direct multiple shooting, the scheme uses an *initial value embedding* initialization that enables an optimal transition from one optimization problem to the next, so only a single Newton-type iteration is performed per sampling time while iterates stay close to the true optimal solutions. First-principles nonlinear models can be reused directly for control.
**Key results** — Method paper; Part II (companion) reports a distillation-column proof-of-concept with reoptimized controls delivered every 20 s on a stiff DAE model with over 200 states.

## Takeaways
- Initial value embedding is the core trick — it warm-starts each QP so one iteration suffices per step.
- Direct multiple shooting lets large first-principles models be reused for real-time control.
- Foundational reference for the real-time iteration / one-iteration-per-step NMPC paradigm.

## Relevance to your work
The real-time iteration scheme underpins practical online NMPC solvers; relevant background for the MPC layer in your tube-based planning work such as [[@compton2025dynamic]].

## Concepts


## Source
- Cited by [[@compton2025learning]]
- bibkeys: `diehl2002efficient`
