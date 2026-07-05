---
type: paper
citekey: marcucci2024fast
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Marcucci, Tobia
- Nobel, Parth
- Tedrake, Russ
- Boyd, Stephen
year: 2024
venue: IEEE Transactions on Robotics
doi: null
arxiv: 2305.01072
url: https://arxiv.org/abs/2305.01072
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@marcucci2024fast.pdf
bibkeys:
- marcucci2024fast
---

# Fast path planning through large collections of safe boxes

> [!info] Marcucci, Tobia; Nobel, Parth; Tedrake, Russ; Boyd, Stephen · 2024 · IEEE Transactions on Robotics

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A fast algorithm that designs smooth, provably safe trajectories constrained to lie within a large collection of axis-aligned safe boxes.
**Problem** — Given many safe boxes covering free space, quickly generate a smooth start-to-goal path guaranteed safe at all times (or certify infeasibility), with heavy preprocessing amortized offline.
**Method** — Precompute box intersections offline; at runtime, reduce the problem to two efficiently-solvable subproblems: a shortest-path search in a weighted graph (over boxes/intersections) followed by (multiple) convex optimal-control problems that shape the smooth trajectory through the chosen box sequence. Detects infeasibility when no such trajectory exists.
**Key results** — Demonstrated on large-scale numerical examples; ships an open-source implementation (fastpathplanning). Emphasis is on runtime speed at large box counts.

## Takeaways
- Decouples the combinatorial (which boxes, via graph shortest path) from the continuous (smooth trajectory, via convex OCP), giving speed and safety-at-all-times guarantees.
- Safe-box decomposition is the enabling primitive; offline preprocessing of intersections keeps online cost low.
- A lighter-weight, axis-aligned-box specialization compared to the more general Graphs-of-Convex-Sets planner ([[@marcucci2023motion]]).

## Relevance to your work
Provides safe convex corridors and smooth trajectories that a locomotion planner can use as the geometric layer; complements reduced-order/tube-based planning where a template must stay inside a safe region, as in [[@hierarchies2025motion]].

## Concepts

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `marcucci2024fast`
