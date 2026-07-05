---
type: paper
citekey: marcucci2024shortest
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Marcucci, Tobia
- Umenberger, Jack
- Parrilo, Pablo
- Tedrake, Russ
year: 2024
venue: SIAM Journal on Optimization
doi: null
arxiv: '2101.11565'
url: https://arxiv.org/abs/2101.11565
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@marcucci2024shortest.pdf
bibkeys:
- marcucci_shortest_2023
---

# Shortest paths in graphs of convex sets

> [!info] Marcucci, Tobia; Umenberger, Jack; Parrilo, Pablo; Tedrake, Russ · 2024 · SIAM Journal on Optimization

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Generalizes the shortest-path problem to graphs whose vertices carry continuous positions constrained to convex sets, with convex edge costs, and gives a tight mixed-integer convex formulation that solves it to global optimality at scale.

**Problem** — Many motion-planning and hybrid optimal-control problems are naturally posed as choosing both a discrete route through a graph and continuous positions at each vertex; solved jointly this "graph of convex sets" (GCS) problem is NP-hard, and naive MICP encodings scale badly.

**Method** — Each vertex position is a continuous decision variable in a convex set and each edge length is a convex function of its endpoints. The main contribution is a strong, lightweight mixed-integer convex programming formulation built on perspective operators, whose convex relaxation is tight enough to recover globally optimal paths efficiently in large graphs and high-dimensional spaces.

**Key results** — Demonstrates efficient global optimization on large graphs and high-dimensional problems where prior formulations are intractable; establishes GCS as a unifying model spanning vehicle motion planning and hybrid-system optimal control.

## Takeaways
- GCS unifies discrete graph search and continuous convex optimization in one tight MICP; the perspective-based relaxation is what makes global optimality tractable.
- Directly applicable to collision-free trajectory optimization (convex safe regions as vertices) and to mode sequencing in hybrid optimal control.
- Still a mixed-integer program at heart — the practical win is the strength of the relaxation, not a polynomial-time guarantee.

## Relevance to your work
GCS underpins modern layered motion planners that hand a kinematic/geometric plan down to a tracking controller; it is the discrete-plus-continuous planning primitive that a hierarchical scheme like [[@hierarchies2025motion]] builds on.

## Concepts


## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `marcucci_shortest_2023`
