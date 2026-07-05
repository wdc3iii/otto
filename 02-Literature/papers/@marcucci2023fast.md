---
type: paper
citekey: marcucci2023fast
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Marcucci, Tobia
- Nobel, Parth
- Tedrake, Russ
- Boyd, Stephen
year: 2023
venue: arXiv:2305.01072 [cs, eess]
doi: null
arxiv: '2305.01072'
url: http://arxiv.org/abs/2305.01072
zotero: null
status: to-read
mine: false
bibkeys:
- marcucci_fast_2023
---

# Fast Path Planning Through Large Collections of Safe Boxes

> [!info] Marcucci, Tobia; Nobel, Parth; Tedrake, Russ; Boyd, Stephen · 2023 · arXiv:2305.01072 [cs, eess]

<!-- SUMMARY-PENDING: ingest-paper will fill a structured summary here -->

## Abstract (from bib)
We present a fast algorithm for the design of smooth paths (or trajectories) that are constrained to lie in a collection of axis-aligned boxes. We consider the case where the number of these safe boxes is large, and basic preprocessing of them (such as ﬁnding their intersections) can be done ofﬂine. At runtime we quickly generate a smooth path between given initial and terminal positions. Our algorithm designs trajectories that are guaranteed to be safe at all times, and it detects infeasibility whenever such a trajectory does not exist. Our algorithm is based on two subproblems that we can solve very efﬁciently: ﬁnding a shortest path in a weighted graph, and solving (multiple) convex optimal control problems. We demonstrate the proposed path planner on large-scale numerical examples, and

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@csomayshanklin2025dynamically]]
- bibkeys: `marcucci_fast_2023`
- arXiv: https://arxiv.org/abs/2305.01072
- URL: http://arxiv.org/abs/2305.01072
