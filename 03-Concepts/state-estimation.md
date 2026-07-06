---
type: concept
tags: [navigation, method, to-revisit]
aliases: [state estimation, LiDAR-inertial odometry, LIO, localization, sensor fusion]
created: 2026-07-06
modified: 2026-07-06
---

# State estimation (LiDAR-inertial odometry / localization)

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
The layer that **fuses proprioception and exteroception (IMU, LiDAR, cameras, kinematics) into a consistent estimate of the robot's state and its pose in the world** — odometry, localization, and the map frame the rest of the stack plans in. Modern approaches include continuous-time / non-uniform trajectory representations for LiDAR-inertial odometry (LIO) and task-agnostic factor-graph fusion of heterogeneous sensors.

## Intuition / why it matters
Perceptive planning is only as good as the frame it runs in: a learned [[forward-dynamics-model]] or an elevation-map-based planner inherits every drift and misalignment from estimation. Several perceptive-locomotion papers name **estimation/mapping as the binding performance constraint** (e.g. BeamDojo's elevation map on FAST-LIO). This concept is the substrate under [[mapless-navigation]] and terrain-aware planning, worth tracking as its own axis.

## Grounding
- [[@nubert2025holistic]] — Holistic Fusion: task- and setup-agnostic robot localization/state estimation.
- [[@quenzel2025lio]] — LIO-MARS: non-uniform continuous-time trajectories for LiDAR-inertial odometry.

## Related
[[mapless-navigation]] · [[traversability-estimation]] · [[forward-dynamics-model]]

## Open questions
- How much estimation drift can a history-aware / revisit-aware navigation policy tolerate before consistency (not perception) becomes the bottleneck?
