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
url: https://arxiv.org/abs/2305.01072
summary: ai-draft
pdf: attachments/@marcucci2023fast.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- marcucci_fast_2023
---

# Fast Path Planning Through Large Collections of Safe Boxes

> [!info] Marcucci, Tobia; Nobel, Parth; Tedrake, Russ; Boyd, Stephen · 2023 · arXiv:2305.01072 [cs, eess]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A fast planner that designs smooth, always-safe trajectories confined to a large collection of axis-aligned safe boxes, with offline preprocessing enabling quick online queries.
**Problem** — When the free space is described by many safe boxes, generating a smooth trajectory between endpoints quickly (and certifying infeasibility) at runtime is the bottleneck.
**Method** — The method splits the work into two efficiently solvable subproblems: finding a shortest path in a weighted graph over the boxes, and solving one or more convex optimal-control problems for the smooth trajectory. Box intersections and other structure are precomputed offline so runtime queries are cheap.
**Key results** — Produces trajectories guaranteed safe at all times and detects infeasibility when no such trajectory exists; demonstrated on large-scale numerical examples with an open-source implementation (`fastpathplanning`).

## Takeaways
- A pragmatic, scalable specialization of the GCS idea to axis-aligned safe boxes — trades generality for speed via offline preprocessing.
- Safety is a hard guarantee (trajectory stays inside the boxes at all times), and infeasibility is detected rather than silently missed.
- Limitation: relies on a precomputed safe-box decomposition of free space; best suited to settings where that decomposition is stable and reusable.

## Abstract (from bib)
We present a fast algorithm for the design of smooth paths (or trajectories) that are constrained to lie in a collection of axis-aligned boxes. We consider the case where the number of these safe boxes is large, and basic preprocessing of them (such as ﬁnding their intersections) can be done ofﬂine. At runtime we quickly generate a smooth path between given initial and terminal positions. Our algorithm designs trajectories that are guaranteed to be safe at all times, and it detects infeasibility whenever such a trajectory does not exist. Our algorithm is based on two subproblems that we can solve very efﬁciently: ﬁnding a shortest path in a weighted graph, and solving (multiple) convex optimal control problems. We demonstrate the proposed path planner on large-scale numerical examples, and

## Relevance to your work
For real-time layered locomotion, a fast box-constrained planner is exactly the kind of high-level trajectory generator that feeds a lower-level tracking controller; it is cited by [[@csomayshanklin2025dynamically]] as a scalable, safety-guaranteed planning primitive.

## Concepts


## Source
- Cited by [[@csomayshanklin2025dynamically]]
- bibkeys: `marcucci_fast_2023`
- arXiv: https://arxiv.org/abs/2305.01072
- URL: http://arxiv.org/abs/2305.01072
