---
type: paper
citekey: gao2018online
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Gao, Fei
- Wu, William
- Lin, Yi
- Shen, Shaojie
year: 2018
venue: 2018 IEEE International Conference on Robotics and Automation (ICRA)
doi: 10.1109/ICRA.2018.8462878
arxiv: null
url: https://doi.org/10.1109/ICRA.2018.8462878
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- gao2018online
---

# Online safe trajectory generation for quadrotors using fast marching method and bernstein basis polynomial

> [!info] Gao, Fei; Wu, William; Lin, Yi; Shen, Shaojie · 2018 · 2018 IEEE International Conference on Robotics and Automation (ICRA)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — An online quadrotor motion planner that fuses fast-marching path search on an ESDF-induced velocity field with piecewise Bézier (Bernstein-basis) trajectory optimization to guarantee the whole trajectory stays inside safe flight corridors.
**Problem** — Generating smooth, dynamically feasible quadrotor trajectories online that are provably collision-free, with good time allocation, in cluttered environments.
**Method** — A fast-marching search runs over a velocity field induced by the map's Euclidean signed distance field (ESDF) to find a path with sensible time allocation; the path is inflated against obstacles to build a convex flight corridor. The trajectory is represented as piecewise Bézier curves in the Bernstein polynomial basis, so its convex-hull property confines positions and higher-order derivatives to the safe corridor, and generation reduces to convex programs.
**Key results** — Demonstrates real-time, collision-free trajectory generation with the safety and dynamic bounds enforced by the Bernstein-basis convex-hull property; open-sourced as HKUST's Btraj.

## Takeaways
- The Bernstein/Bézier convex-hull property is the key trick: bounding control points bounds the entire curve (and its derivatives) inside safe convex regions.
- ESDF-driven fast marching gives better time allocation than naive geometric search.
- Enforces safety as hard constraints in a convex program rather than as a soft penalty.

## Relevance to your work
A canonical safe-corridor + polynomial-optimization planner; useful as the aerial-robotics counterpoint to legged safe motion generation and the kind of high-level planner a [[@hierarchies2025motion]] hierarchy would sit atop.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `gao2018online`
