---
type: paper
citekey: ames2016barrier
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Ames, Aaron D
- Xu, Xiangru
- Grizzle, Jessy W
- Tabuada, Paulo
year: 2016
venue: IEEE Transactions on Automatic Control
doi: 10.1109/TAC.2016.2638961
arxiv: '1609.06408'
url: https://arxiv.org/abs/1609.06408
summary: ai-draft
pdf: attachments/@ames2016barrier.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- ames2016control
---

# Control barrier function based quadratic programs for safety critical systems

> [!info] Ames, Aaron D; Xu, Xiangru; Grizzle, Jessy W; Tabuada, Paulo · 2016 · IEEE Transactions on Automatic Control

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — The canonical journal treatment of control barrier functions, unifying safety and performance in a quadratic program and formalizing two generalizations of barrier functions guaranteeing forward set invariance.

**Problem** — Safety-critical systems tightly couple potentially conflicting control objectives and safety constraints; a formal framework is needed to enforce safety while pursuing performance in real-time optimization-based control.

**Method** — Safety is specified as forward invariance of a set and verified via two novel generalizations of barrier functions; in each case a barrier function satisfying Lyapunov-like conditions implies forward invariance, and the relationship between the two classes is characterized. Each yields a control barrier function (CBF) giving affine inequality constraints on the input, which are unified with control Lyapunov functions (CLFs) in a QP so control objectives are met subject to admissible-state constraints.

**Key results** — Demonstrates the CBF-CLF-QP mediating safety and performance on two automotive problems with actuator bounds — adaptive cruise control and lane keeping.

## Takeaways
- The reference formulation for CBFs: zeroing/reciprocal barrier constructions, forward invariance, and their relationship rigorously characterized.
- CBF-CLF-QP is the workhorse pointwise safety-critical controller; safety enters as a linear inequality compatible with real-time QP solves.
- Validation is automotive (ACC, lane keeping) with actuator limits — the extension to legged/high-dimensional systems is left to later work.

## Relevance to your work
The foundational CBF reference underlying safety filters and safe learning in your control/locomotion pipelines ([[@compton2025learning]]); the QP-based safety-performance mediation is the standard tool you build on.

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025learning]]
- bibkeys: `ames2016control`
