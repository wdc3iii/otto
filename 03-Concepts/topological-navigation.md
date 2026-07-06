---
type: concept
tags: [navigation, planning, to-revisit]
aliases: [topological navigation, topological map, image-goal navigation]
created: 2026-07-06
modified: 2026-07-06
---

# Topological navigation

> [!note] Stub — expand when revisited.

## Definition
Navigating over a **sparse graph of observations (nodes) connected by navigable edges**, planned with a goal-directed heuristic — instead of a dense metric SLAM map. Goals are often specified as **target images** (image-goal navigation). The GNM→ViNT→NoMaD line pairs this with high-capacity, embodiment-agnostic goal-conditioned policies pre-trained across robots for zero-shot transfer.

## Why it matters
The longer-horizon direction for the [[capability-aware-navigation]] project: a topological/semantic layer over the dense local policy, optionally with OpenStreetMap as a campus prior. Candidate novelty recorded here — none of this (wheeled-robot) topo-nav work addresses **capability-annotated edges** (walkable / runnable / stairs) for a multi-gait humanoid; that is the open gap. Complements [[mapless-navigation]] (which is the dense/reactive half — this is the graph-planning half).

## Grounding
- [[@shah2023gnm]] — general (embodiment-agnostic) navigation model. · [[@shah2023vint]] — visual-navigation foundation model + topological planning. · [[@sridhar2024nomad]] — goal-masked diffusion unifying navigation + exploration.

## See also
[[mapless-navigation]] · [[recurrent-navigation-policy]] · [[capability-aware-navigation]]
