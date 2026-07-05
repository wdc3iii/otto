---
type: paper
citekey: marcucci2021shortest
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Marcucci, T.
- Umenberger, J.
- Parrilo, P. A.
- Tedrake, R.
year: 2021
venue: arXiv:2101.11565
doi: null
arxiv: '2101.11565'
url: https://arxiv.org/abs/2101.11565
summary: ai-draft
pdf: attachments/@marcucci2021shortest.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- marcucci2021shortest
---

# Shortest paths in graphs of convex sets

> [!info] Marcucci, T.; Umenberger, J.; Parrilo, P. A.; Tedrake, R. · 2021 · arXiv:2101.11565

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Introduces the Graphs of Convex Sets (GCS) framework: a shortest-path problem where each vertex's position is a continuous variable constrained to a convex set and edge lengths are convex functions, solved via a tight mixed-integer convex formulation.
**Problem** — Classical shortest-path assumes fixed vertex positions. Many robotics and hybrid-control problems instead need shortest paths where vertices live in convex sets and costs are convex — a problem that is NP-hard in general.
**Method** — The authors formulate this generalized shortest-path problem and give a strong, lightweight mixed-integer convex program based on perspective operators. The formulation's convex relaxation is tight enough to find globally optimal paths efficiently in large graphs and high-dimensional spaces.
**Key results** — Demonstrated to efficiently recover globally optimal paths on large graphs and in high dimensions; positioned as broadly applicable, from autonomous-vehicle motion planning to optimal control of hybrid systems.

## Takeaways
- GCS is the foundational primitive underlying a family of convex-optimization motion planners (obstacle avoidance, trajectory optimization).
- The perspective-based MICP formulation yields tight relaxations, so global optimality is practically attainable — the key contrast with prior mixed-integer planners.
- Assumption/limitation: convexity of the per-vertex sets and edge costs; problem is NP-hard, so tightness of the relaxation is what makes it tractable.

## Relevance to your work
GCS is the mathematical backbone of the convex-optimization motion planners that a layered locomotion pipeline like [[@csomayshanklin2025dynamically]] uses at the planning layer — turning cluttered, combinatorial routing into a single tight convex program.

## Concepts


## Source
- Cited by [[@csomayshanklin2025dynamically]]
- bibkeys: `marcucci2021shortest`
- arXiv: https://arxiv.org/abs/2101.11565
