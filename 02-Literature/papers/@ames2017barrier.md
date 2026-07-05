---
type: paper
citekey: ames2017barrier
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- A. D. Ames
- X. Xu
- J. W. Grizzle
- P. Tabuada
year: 2017
venue: TAC
doi: 10.1109/TAC.2016.2638961
arxiv: null
url: https://doi.org/10.1109/TAC.2016.2638961
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- AmesTAC17
---

# Control barrier function based quadratic programs for safety critical systems

> [!info] A. D. Ames; X. Xu; J. W. Grizzle; P. Tabuada · 2017 · TAC

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Establishes control barrier functions (CBFs) as inequality constraints that guarantee forward invariance (safety) of a set, and unifies them with control Lyapunov functions (CLFs) inside a single real-time quadratic program.
**Problem** — Safety-critical systems couple potentially conflicting control objectives and safety constraints; the paper builds a formal framework to enforce safety while pursuing performance, with automotive applications in view.
**Method** — Safety is cast as forward invariance of a set, verified via two novel generalizations of barrier functions, each satisfying Lyapunov-like conditions that imply invariance; the relationship between the two classes is characterized. Each yields a CBF giving an affine inequality constraint on the input, which is combined with CLF performance objectives in a QP solved online.
**Key results** — A constructive, real-time CBF-CLF-QP methodology that provably renders a safe set forward invariant; foundational formulation later applied across robotics and autonomous driving. (TAC, published 2016 / 2017.)

## Takeaways
- The canonical CBF-QP formulation: safety as forward set invariance, encoded as a linear-in-input inequality that a QP enforces every timestep.
- CBFs unify with CLFs in one QP, mediating safety-vs-performance conflicts pointwise; safety takes precedence via a hard constraint.
- Two barrier-function generalizations (zeroing/reciprocal-style) are introduced and related — the theoretical backbone for most later CBF work.

## Relevance to your work
The foundational reference for control-barrier-function safety filters that underlies essentially all CBF-based safe control, including [[@cohen2025safety]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@cohen2025safety]]
- bibkeys: `AmesTAC17`
