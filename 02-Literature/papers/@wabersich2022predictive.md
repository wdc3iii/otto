---
type: paper
citekey: wabersich2022predictive
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Wabersich, Kim P
- Zeilinger, Melanie N
year: 2022
venue: IEEE Transactions on Automatic Control
doi: 10.1109/TAC.2022.3175628
arxiv: 2105.10241
url: https://arxiv.org/abs/2105.10241
summary: ai-draft
pdf: attachments/@wabersich2022predictive.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- wabersich2022predictive
---

# Predictive control barrier functions: Enhanced safety mechanisms for learning-based control

> [!info] Wabersich, Kim P; Zeilinger, Melanie N · 2022 · IEEE Transactions on Automatic Control

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A predictive-control formulation of CBFs that adds an always-feasible soft-constrained MPC problem, giving learning-based controllers a recovery mechanism when a predictive safety filter would otherwise fail.

**Problem** — Learning-based controllers often outperform classical designs but lack safety guarantees. Predictive safety filters can enforce safety, but their guarantees rely on model assumptions; minor model deviations can make the filter infeasible and put the system at risk.

**Method** — The paper introduces an auxiliary soft-constrained predictive control problem that is feasible at every time step and asymptotically stabilizes the feasible set of the original safety filter. This is achieved through simple constraint tightening combined with a terminal control barrier function, yielding a "predictive CBF" that recovers safety after violations.

**Key results** — Provides a recovery mechanism that restores the system to the safe feasible set even under model mismatch, extending the reliability of predictive safety filters for learning-based control.

## Takeaways
- Terminal-CBF + constraint tightening makes the safety MPC recursively feasible by construction — no hard infeasibility cliff.
- Reframes safety filtering as attraction toward the feasible set, not just constraint satisfaction, giving graceful recovery.
- Bridges MPC and CBF viewpoints: the terminal ingredient is the CBF.

## Relevance to your work
A core reference for combining MPC-style prediction with CBF safety under model uncertainty — the recursive-feasibility and recovery machinery is directly pertinent to safe learning-based control as in [[@compton2025learning]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025learning]]
- bibkeys: `wabersich2022predictive`
