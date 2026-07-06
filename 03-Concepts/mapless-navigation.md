---
type: concept
tags: [navigation, to-revisit]
aliases: [mapless navigation, map-free navigation, long-horizon mapless navigation]
created: 2026-07-06
modified: 2026-07-06
---

# Mapless navigation

> [!note] Stub — minimal seed, expand when revisited.

## Definition
Navigating to a goal **without a prior metric map and without an online SLAM/localization module continuously updating self- and goal-position**. The policy reasons from raw onboard sensing (proprioception, depth/RGB) and whatever spatial context it can maintain internally. The hard version is **long-horizon** mapless navigation: escaping dead ends and local minima in maze-like layouts under partial observability, where purely reactive policies get trapped.

## Why it matters
Removing the map/localizer is what makes a policy genuinely **end-to-end** and cheap to deploy — but it shifts the burden onto the policy to hold a persistent sense of direction. Open question: how much internal spatial memory can a learned policy sustain, and can it approach the "cognitive map" behavior seen in animals?

## Grounding
- [[@wang2026guide]] — goal-initialized setting (target given only at $t=0$); internal egomotion via a spatial-anchor auxiliary predictor.
- Dense/reactive learned nav: [[@yang2025spatially]] (SRU spatial memory) · [[@hoeller2021learning]] (VAE+LSTM) · [[@lee2024learning]] (km-scale HRL) · [[@zhang2026focusnav]] (humanoid local nav) · [[@haro2026path]] · [[@roth2025learned]] (FDM+MPPI) · [[@wijmans2019ddppo]].
- Topological/graph half: [[@shah2023gnm]] · [[@shah2023vint]] · [[@sridhar2024nomad]] → see [[topological-navigation]].

## See also
- [[rl-for-legged-locomotion]] · [[sim-to-real-transfer]] · [[recurrent-navigation-policy]] · [[topological-navigation]] · [[capability-aware-navigation]]
