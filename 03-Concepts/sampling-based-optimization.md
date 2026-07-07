---
type: concept
tags: [planning, control, to-revisit]
aliases: [sampling-based optimization, MPPI, sampling-based MPC, sampling-based trajectory optimization, derivative-free optimization]
created: 2026-07-06
modified: 2026-07-07
---

# Sampling-based optimization (MPPI)

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
Trajectory optimization that **samples many candidate action sequences, rolls them out through a (possibly learned) dynamics model, and forms an update from the cost-weighted samples** — rather than differentiating the dynamics/cost. Model Predictive Path Integral (MPPI) is the canonical instance: importance-weight rollouts by exponential cost and take the weighted-mean action. Derivative-free, trivially parallel, and indifferent to non-smooth or learned models.

## Intuition / why it matters
It is the planner that pairs naturally with a learned [[forward-dynamics-model]]: the FDM supplies fast batched rollouts + a risk head, and the sampler needs no gradients through it. That makes "learn the dynamics, sample the plan" a complete [[informed-locomotion-planning|informed-planning]] recipe — the contrast case to gradient-based [[tube-mpc]]. The trade-off is sample efficiency and the need to tune the action distribution (command ranges, time correlation).

## Grounding
- [[@tracy2025trajectory]] — the Trajectory Bundle Method: derivative-free trajectory optimization over sampled rollouts (unifying sequential-convex / sampling ideas).
- [[@roth2025learned]] — MPPI optimizes velocity commands against the learned FDM + risk threshold.
- [[@pezzato2023sampling]] — "Sampling-based MPC": an MPPI controller using a GPU-parallel physics simulator directly as its model.
- [[@williams2001robust]] — the MPPI-robustness paper: fuses sampling-based MPC with linearization inside a robust tube.
- [[@gibson2023multi]] — a multi-step learned dynamics model built to stay scalable for sampling-based (MPPI) control.

## Related
[[forward-dynamics-model]] · [[tube-mpc]] · [[informed-locomotion-planning]]

## Open questions
- How much of MPPI's tuning burden (action distribution, horizon, temperature) can be absorbed by the learned model or a warm-start from a reduced-order plan?
