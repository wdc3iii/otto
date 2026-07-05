---
type: paper
citekey: khazoom2024tailoring
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Charles Khazoom
- Seungwoo Hong
- Matthew Chignoli
- Elijah Stanger-Jones
- Sangbae Kim
year: 2024
venue: preprint arXiv:2407.10789
doi: https://doi.org/10.1109/LRA.2024.3455907
arxiv: '2407.10789'
url: https://arxiv.org/abs/2407.10789
summary: ai-draft
pdf: attachments/@khazoom2024tailoring.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- khazoom2024humanoid
---

# Tailoring Solution Accuracy for Fast Whole-body Model Predictive Control of Legged Robots

> [!info] Charles Khazoom; Seungwoo Hong; Matthew Chignoli; Elijah Stanger-Jones; Sangbae Kim · 2024 · preprint arXiv:2407.10789

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Deliberately solving whole-body NMPC to *low* accuracy (via a fast ADMM QP inner loop) is enough for real legged robots and lets whole-body NMPC run on hardware at 90 Hz.

**Problem** — Whole-body NMPC for humanoids is now near-real-time, but enforcing inequality constraints on such high-dimensional systems needs extra solver iterations that are too expensive; highly accurate optimal solutions may not even pay off given model/discretization errors.

**Method** — Rather than chasing accurate optima, they use ADMM to rapidly return low-accuracy solutions to the QP subproblems within NMPC, handling general equality/inequality constraints. Control barrier functions are injected at the NMPC's initial timestep to enforce self-collision constraints cheaply.

**Key results** — Up to a 26-fold reduction in self-collisions from the initial-timestep CBFs with no added compute; deployed on the MIT Humanoid at 90 Hz for a problem with 32 timesteps, 2004 variables, and 3768 constraints, enabling crossed-leg and arm motions that improve balance and disturbance recovery.

## Takeaways
- Central insight: solver accuracy is often not the bottleneck — dynamics discretization, inertial modeling errors, and delays dominate, so low-accuracy NMPC solutions suffice.
- ADMM as the inner QP solver trades exactness for speed; CBFs used only at the first timestep are a cheap way to buy hard-constraint satisfaction (self-collision here).
- Concrete real-time hardware result at 90 Hz on a full humanoid with thousands of constraints.

## Relevance to your work
A pragmatic point on the accuracy/speed frontier of whole-body MPC for humanoids, and a nice example of embedding a [[control-barrier-function]] inside an MPC to get hard safety/self-collision constraints cheaply — directly relevant to real-time MPC-based locomotion pipelines like [[@csomayshanklin2024robust]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@csomayshanklin2024robust]]
- bibkeys: `khazoom2024humanoid`
- arXiv: https://arxiv.org/abs/2403.03995
