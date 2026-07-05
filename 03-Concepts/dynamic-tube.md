---
type: concept
tags: [control, rl, to-revisit]
aliases: [dynamic tube, learned tube]
created: 2026-07-05
modified: 2026-07-05
---

# Dynamic tube

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
A learned, **action-dependent** error tube whose width is a function of the planning model's trajectory (and error history), rather than a single worst-case bound — trained to be an α-quantile of the observed tracking error.

## Intuition / why it matters
Some reference trajectories are easier to track than others; a dynamic tube exploits this, shrinking where tracking is easy and widening where it's hard, so the planner can trade performance against safety **in real time**. Conditioning the tube on the *error history* (rather than instantaneous error alone) is the key idea — it acts like a filter that distinguishes states with equal instantaneous error but different trends.

## Grounding
- [[@compton2025dynamic]] — the contribution (learn tube dynamics from parallel sim, deploy in MPC on ARCHER).
- [[@fan2020deep]] — deep-learning-tubes prior art it extends.

## Related
- [[tube-mpc]] · [[tracking-error-bound]] · [[massively-parallel-simulation]]

## Open questions
- Distribution shift between random training trajectories and MPC-generated ones (the paper's stated limitation).
