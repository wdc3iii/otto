---
type: concept
tags: [navigation, rl, to-revisit]
aliases: [path-conditioned RL, path conditioning, condition-not-constrain]
created: 2026-07-06
modified: 2026-07-06
---

# Path-conditioned RL

> [!note] Stub — expand when revisited.

## Definition
Conditioning a navigation/locomotion RL policy on a **reference path as a soft observation, not a hard follow-constraint**: the reward stays purely goal-reaching, and the path is provided only as an input the policy can opportunistically exploit when it's good and ignore when it's bad. Yields graceful degradation under an imperfect path prior.

## Why it matters
The natural interface for the [[capability-aware-navigation]] project's **walkable-path segmentation** workstream: a segmented sidewalk/path becomes a conditioning signal for the mid-level [[recurrent-navigation-policy]] rather than a rigid trajectory to track. The "condition, don't constrain" principle generalizes to any imperfect perceptual prior.

## Grounding
- [[@haro2026path]] — path-conditioned RL local planner for long-range navigation.

## See also
[[recurrent-navigation-policy]] · [[mapless-navigation]] · [[capability-aware-navigation]]
