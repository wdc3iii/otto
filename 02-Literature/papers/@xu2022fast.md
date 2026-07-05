---
type: paper
citekey: xu2022fast
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Xu, Wei
- Cai, Yixi
- He, Dongjiao
- Lin, Jiarong
- Zhang, Fu
year: 2022
venue: IEEE Transactions on Robotics
doi: 10.1109/TRO.2022.3141876
arxiv: '2107.06829'
url: https://arxiv.org/abs/2107.06829
summary: ai-draft
pdf: attachments/@xu2022fast.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- xu2022fast
---

# Fast-lio2: Fast direct lidar-inertial odometry

> [!info] Xu, Wei; Cai, Yixi; He, Dongjiao; Lin, Jiarong; Zhang, Fu · 2022 · IEEE Transactions on Robotics

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — FAST-LIO2 is a fast, robust, versatile LiDAR-inertial odometry framework that registers raw points directly to the map (no feature extraction) and maintains the map with an incremental k-d tree (ikd-Tree).

**Problem** — Feature-extraction front-ends discard information and are LiDAR-specific, while conventional map structures are too slow to update for high-rate direct registration.

**Method** — Builds on an efficient tightly-coupled iterated Kalman filter with two novelties: (1) direct registration of raw points to the map, avoiding hand-designed feature extraction and exploiting subtle environment structure; (2) an incremental k-d tree (ikd-Tree) supporting incremental insertion/deletion and dynamic re-balancing for efficient map maintenance.

**Key results** — Up to 100 Hz odometry/mapping in large outdoor scenes; robust pose estimation in cluttered indoor settings under rotation up to 1000 deg/s; works across spinning and solid-state LiDARs, UAV/handheld platforms, and Intel/ARM processors, with higher accuracy than prior methods. Open-sourced.

## Takeaways
- Direct raw-point registration removes the feature-engineering step and generalizes across LiDAR types.
- The ikd-Tree is the enabling data structure — incremental, self-rebalancing map maintenance keeps direct registration real-time.
- Successor to FAST-LIO; a widely-used, production-grade odometry/mapping backbone.

## Relevance to your work
High-rate, accurate LiDAR-inertial mapping is the perception layer feeding terrain elevation and localization to legged navigation stacks such as [[@terrain2026consistent]].

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `xu2022fast`
