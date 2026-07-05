---
type: concept
tags: [rl, to-revisit]
aliases: [massively parallel simulation, parallel simulation, GPU simulation]
created: 2026-07-05
modified: 2026-07-05
---

# Massively parallel simulation

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
Simulating thousands of environment instances at once on a single GPU (e.g. Isaac Gym), enabling data collection and RL/learning at orders-of-magnitude higher throughput than CPU simulation.

## Intuition / why it matters
Throughput is the enabler: it makes data-hungry methods practical on one workstation — RL locomotion policies, but also **learned tube dynamics** and **learned CBF robustification** in your work. The standing catch is sim-to-real / distribution shift, mitigated with domain randomization.

## Grounding
- [[@rudin2021learning]] · [[@makoviychuk2021isaac]] — the recipe and the engine.
- [[@compton2025dynamic]] — 8192 envs to learn tube dynamics.
- [[@compton2025learning]] — learns a CBF robustness term via parallel sim + domain randomization.

## Related
- [[dynamic-tube]]

## Open questions
- Closing the gap between random-input training data and the deployment distribution.
