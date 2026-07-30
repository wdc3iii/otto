---
type: concept
tags: [navigation, planning, to-revisit]
aliases: [traversability estimation, traversability]
created: 2026-07-06
modified: 2026-07-29
---

# Traversability estimation

> [!note] Stub — expand when revisited.

## Definition
Assessing **where a specific platform can safely move** — a cost/feasibility field over terrain — whether via hand-designed heuristics (slope, roughness, step height), geometric cost-maps, or **learned** models that predict future states and failure risk from perception + a candidate action sequence.

## Why it matters
The problem frame beneath both the "walkable-path" (semantic: sidewalk vs. grass) and "capability" (dynamic: can this gait clear this step?) legs of the [[capability-aware-navigation]] project. A *learned* traversability/forward-dynamics model ([[@roth2025learned]]) is an alternative route to [[capability-awareness]] — model-predictive rather than a reward regularizer on the LLC's Lyapunov value.

## Grounding
- [[@roth2025learned]] — learned perceptive forward-dynamics model for platform-aware navigation.
- *Added 2026-07-29* — terrain/occupancy as an **estimated module** vs. an **auxiliary head**, the architectural fork in [[auxiliary-prediction-heads]]: [[@ren2024topnav]] (TOP-Nav — explicit terrain/obstacle estimator corrected online by proprioception) · [[@shi2026oneocc]] (semantic occupancy for legged robots, single panoramic camera) · [[@miki2022learning]] (reconstructing a noiseless heightmap from a recurrent belief). See [[occupancy-anticipation]].

## See also
[[capability-awareness]] · [[mapless-navigation]] · [[social-navigation]]
