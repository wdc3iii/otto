---
type: paper
citekey: kuindersma2016optimization
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Kuindersma, Scott
- Deits, Robin
- Fallon, Maurice
- Valenzuela, Andr\'es
- Dai, Hongkai
- Permenter, Frank
- Koolen, Twan
- Marion, Pat
- Tedrake, Russ
year: 2016
venue: Autonomous robots
doi: 10.1007/s10514-015-9479-3
arxiv: null
url: https://doi.org/10.1007/s10514-015-9479-3
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- kuindersma2016optimization
---

# Optimization-based locomotion planning, estimation, and control design for the atlas humanoid robot

> [!info] Kuindersma, Scott; Deits, Robin; Fallon, Maurice; Valenzuela, Andr\'es; Dai, Hongkai; Permenter, Frank · 2016 · Autonomous robots

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A consolidated account of the MIT DARPA Robotics Challenge stack: a family of optimization algorithms spanning footstep planning, whole-body planning/control, and state estimation for the Atlas hydraulic humanoid.
**Problem** — Achieving reliable dynamic planning, control, and estimation for a full-size bipedal humanoid operating in complex, unstructured environments.
**Method** — Applies convex, mixed-integer, and sparse nonlinear optimization across the stack: mixed-integer/convex programs for footstep placement, trajectory optimization for whole-body plans, and QP-based whole-body control, integrated with state estimation. Validated on Atlas, the Boston Dynamics hydraulic humanoid.
**Key results** — Demonstrates the integrated pipeline running on real hardware for locomotion and manipulation tasks in the DRC setting; a widely cited reference architecture for optimization-based humanoid control.

## Takeaways
- Canonical example of a layered, optimization-based humanoid stack: reduced-model footstep planning atop QP whole-body control.
- Shows how heterogeneous optimization classes (MIQP for combinatorial footstep choice, sparse NLP for trajectories, QP for instantaneous control) compose into one system.
- Hardware-validated on a large hydraulic humanoid — a real-world stress test, not just simulation.

## Relevance to your work
A reference point for the classical planning-and-control hierarchy that RL locomotion policies now compete with or augment; [[@hierarchies2025motion]] situates its layered motion-generation ideas against exactly this kind of optimization-based whole-body stack.

## Concepts
[[hierarchical-control]] · [[reduced-order-model]]

## Source
- Cited by [[@compton2024constructive]], [[@hierarchies2025motion]]
- bibkeys: `kuindersma2016optimization`
