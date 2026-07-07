---
type: concept
tags: [navigation, planning, to-revisit]
aliases: [forward dynamics model, FDM, learned forward dynamics, learned dynamics model]
created: 2026-07-06
modified: 2026-07-07
---

# Forward-dynamics model (FDM)

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
A **learned predictor of what the platform will actually do** given a candidate action/command sequence and its current perception: it maps (state history, proprioception, terrain/height scan, commands) → future states (e.g. an $SE(2)$ pose rollout) and, crucially, a **failure/collision risk**. A sampling planner (typically [[sampling-based-optimization|MPPI]]) then optimizes the commands against a goal subject to a risk threshold. The FDM models the *emergent dynamics of a specific deployed controller on specific terrain*, not rigid-body physics.

## Intuition / why it matters
The FDM is the **learned** answer to the [[reduced-order-model|RoM↔FoM gap]]: instead of certifying a [[tracking-error-bound]] and planning inside a [[tube-mpc|tube]], you *learn* the achievable set and where the controller fails, and plan against that. It's an alternative, model-predictive route to [[capability-awareness]] — the risk head *is* a learned capability boundary — and it collapses explicit [[traversability-estimation]] into a predictive query. The cost: it is only as good as its training distribution (geometry-bound, controller-bound), with no guarantee — the central tension of [[informed-locomotion-planning]].

## Grounding
- [[@roth2025learned]] — learned perceptive FDM predicting future pose **and** failure risk; the closest prior art to my humanoid FDM line.
- [[@kim2022forward]] — learning a forward-dynamics model + informed trajectory selection.
- [[@gibson2023multi]] — a multi-step dynamics-modeling framework for autonomous off-road driving.
- [[@lee2023terrain]] — learned terrain-aware kinodynamic model for planning.
- [[@pokhrel2024cahsor]] — competence-aware learned 6-DoF model that respects platform limits.
- [[@beyer2024risk]] — learned riskmaps for risk-predictive off-road planning.
- [[@kahn2020badgr]] — BADGR: self-supervised learned model of navigation outcomes (collision/bumpiness/position), planned against; the affordance-over-geometry FDM precedent.

## Related
[[capability-awareness]] · [[traversability-estimation]] · [[sampling-based-optimization]] · [[tube-mpc]] · [[reduced-order-model]] · [[informed-locomotion-planning]]

## Open questions
- Latent vs. explicit environment encoding; carrying history across revisits; and making the risk head *conservative under perceptual uncertainty* — my three intended extensions (see [[@roth2025learned]] notes).
- Should the learned capability boundary be a **hard** forward-invariance constraint (CBF/tube) or a **soft learned cost** (FDM risk)?
