---
type: concept
tags: [control, planning, to-revisit]
aliases: [contact-implicit MPC, whole-body NMPC, contact-implicit optimization]
created: 2026-07-06
modified: 2026-07-07
---

# Contact-implicit MPC

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
Nonlinear model-predictive control over the **full-order** dynamics in which **contact locations and timings are decision variables**, discovered by the optimizer, rather than prescribed by a fixed gait schedule or contact sequence. The optimizer reasons directly about when and where to make/break contact as part of the trajectory optimization.

## Intuition / why it matters
This sits at the opposite end of my MPC spectrum from [[reduced-order-model|reduced-order]] / [[tube-mpc|tube]] planning: maximal fidelity and generality (no hand-specified contacts) at the cost of a hard, contact-rich nonconvex optimization that must run fast enough for control. Useful as the "high-fidelity, no-abstraction" reference point when arguing for why ROM + tracking-guarantee approaches are worth their conservatism.

## Grounding
- [[@neunert2018whole]] — whole-body nonlinear MPC through contact for legged robots.

## Related
[[reduced-order-model]] · [[tube-mpc]] · [[hierarchical-control]] · [[step-to-step-dynamics]] — the *opposite pole* on "how much contact reasoning lives in the planner": S2S/H-LIP **prescribes** a fixed contact sequence on a reduced model and chooses only foot placement; contact-implicit MPC **discovers** contact timing/location on the full model. Together they bracket the spectrum.

## Open questions
- Where is the real-time frontier — how much contact-implicit reasoning is affordable online on the G1 vs. offloaded to an offline/reference layer?
