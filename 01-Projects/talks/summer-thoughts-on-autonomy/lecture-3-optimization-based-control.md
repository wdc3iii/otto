---
type: project
tags: [control]
aliases: [Optimization-Based Control]
created: 2026-07-06
recorded: 2026-07-03
video: https://youtu.be/fY6IJ6qSb-E
series: "[[summer-thoughts-on-autonomy]]"
modified: 2026-07-06
---

# Lecture 3 — Optimization-Based Control

Part of [[summer-thoughts-on-autonomy|Summer Thoughts on Autonomy]] · recorded 2026-07-03 ·
[watch](https://youtu.be/fY6IJ6qSb-E)

## Summary (from the lecture description)
A tour of optimization-based control schemes: starting from the **principle of optimality**
and the **HJB equation**, moving through **trajectory optimization** and transcription
methods, and commenting on **receding-horizon control** and real-time iterations.

## Key ideas
- **Principle of optimality → HJB** — the dynamic-programming foundation of optimal control.
- **Trajectory optimization & transcription** — turning the optimal-control problem into a
  finite nonlinear program (direct/indirect, shooting vs. collocation).
- **Receding-horizon control (MPC)** and **real-time iteration** — solving the problem
  online, repeatedly, under a compute budget.

> [!note] Expand with your own framing/slides — distilled from the public description.

## Connections in otto
- Receding-horizon control is the backbone of [[tube-mpc]] and [[dynamic-tube]] MPC, realized
  in [[@compton2025dynamic]]; the layered use of optimization appears in [[hierarchical-control]].
- Grounds the classical half of the "structure" axis raised in [[lecture-1-open-problems]].
