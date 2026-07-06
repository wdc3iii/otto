---
type: project
tags: [rl]
aliases: [Simulation and Digital Validation]
created: 2026-07-06
recorded: 2026-06-29
video: https://youtu.be/g-YIiTq3JI8
series: "[[summer-thoughts-on-autonomy]]"
modified: 2026-07-06
---

# Lecture 2 — Simulation and Digital Validation

Part of [[summer-thoughts-on-autonomy|Summer Thoughts on Autonomy]] · recorded 2026-06-29 ·
[watch](https://youtu.be/g-YIiTq3JI8)

## Summary (from the lecture description)
A discussion of simulators and synthetic data generation, organized along three dimensions
— **fidelity**, **throughput**, and **coverage** — and the trade-offs among them when using
the digital world to validate autonomy.

## Key ideas
- **Fidelity** — how faithfully the simulator matches reality (the sim-to-real gap).
- **Throughput** — how much experience/data you can generate per unit time.
- **Coverage** — how much of the relevant scenario/state space you actually exercise.
- These three pull against each other; the right simulator depends on what you're validating.

> [!note] Expand with your own framing/slides — distilled from the public description.

## Connections in otto
- Throughput-at-scale is exactly what [[massively-parallel-simulation]] buys, and what the
  tube-dynamics / PCBF training in [[@compton2025dynamic]] and [[@compton2025learning]] rely on.
- Fidelity/coverage vs. the sim-to-real gap connects to domain randomization used across the
  hardware-deployed policies ([[@dai2025walk]], [[@terrain2026consistent]]).
