---
type: paper
citekey: ames2014barrier
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Ames, Aaron D
- Grizzle, Jessy W
- Tabuada, Paulo
year: 2014
venue: 53rd IEEE conference on decision and control
doi: 10.1109/CDC.2014.7040372
arxiv: null
url: https://doi.org/10.1109/CDC.2014.7040372
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- ames2014control
---

# Control barrier function based quadratic programs with application to adaptive cruise control

> [!info] Ames, Aaron D; Grizzle, Jessy W; Tabuada, Paulo · 2014 · 53rd IEEE conference on decision and control

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces the control-barrier-function quadratic program (CBF-QP) that unifies safety (CBFs) and performance (CLFs) in a single optimization, demonstrated on adaptive cruise control.

**Problem** — Safety-critical control must reconcile potentially conflicting objectives — achieving performance goals while respecting hard safety constraints and actuator bounds — in real time.

**Method** — Presents a barrier function tied to a set via Lyapunov-like conditions whose existence implies forward invariance of the set, yielding a control barrier function (CBF) that imposes an affine inequality constraint on the control input. CBFs are then unified with control Lyapunov functions (CLFs) inside a quadratic program, so performance objectives (CLF) are pursued subject to safety constraints (CBF) and input bounds.

**Key results** — The CBF-CLF-QP is illustrated on adaptive cruise control, balancing a desired-speed objective against minimum-following-distance safety and force/acceleration/braking limits.

## Takeaways
- The seminal formulation of the CBF-CLF-QP pointwise controller — safety as forward set invariance encoded as a linear inequality in u.
- Mediating safety vs. performance through a QP makes real-time safety-critical control tractable with actuator bounds.
- Conference precursor to the fuller TAC treatment ([[@ames2016barrier]]).

## Relevance to your work
The origin of the CBF-QP that underpins safety filters in modern control and learning-based locomotion pipelines ([[@compton2025learning]]).

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025learning]]
- bibkeys: `ames2014control`
