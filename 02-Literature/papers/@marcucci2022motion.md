---
type: paper
citekey: marcucci2022motion
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Marcucci, Tobia
- Petersen, Mark
- von Wrangel, David
- Tedrake, Russ
year: 2022
venue: arXiv:2205.04422 [cs]
doi: null
arxiv: '2205.04422'
url: https://arxiv.org/abs/2205.04422
summary: ai-draft
pdf: attachments/@marcucci2022motion.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- marcucci_motion_2022
---

# Motion Planning around Obstacles with Convex Optimization

> [!info] Marcucci, Tobia; Petersen, Mark; von Wrangel, David; Tedrake, Russ · 2022 · arXiv:2205.04422 [cs]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Shows that convex optimization can reliably plan collision-free trajectories around obstacles by combining Bézier curves with the Graphs of Convex Sets (GCS) framework, yielding a compact mixed-integer program with a very tight relaxation.
**Problem** — Obstacle-cluttered configuration spaces make trajectory optimization nonconvex, so roboticists fall back to sampling-based planners that struggle in high dimensions and with continuous differential constraints.
**Method** — The authors formulate planning with collision-avoidance constraints plus cost/hard constraints on trajectory shape, duration, and velocity as a compact mixed-integer optimization, using Bézier-curve properties inside the GCS framework. Because the convex relaxation is tight, a cheap rounding usually yields globally optimal trajectories, effectively reducing the MIP to a convex program while providing optimality bounds.
**Key results** — Demonstrated on a quadrotor flying through buildings and a 14-DOF dual-arm manipulator in confined space; on a 7-DOF manipulator, GCS finds higher-quality trajectories in less time than widely-used sampling-based planners.

## Takeaways
- Directly challenges the assumption that obstacle-rich motion planning must be nonconvex/sampling-based — convex optimization can be made reliable here.
- The tight relaxation is the crux: cheap rounding recovers global optimality and yields optimality certificates, unlike prior mixed-integer planners.
- Scales to high-DOF systems (14-DOF dual arm) with continuous differential constraints — a regime where sampling planners degrade.

## Abstract (from bib)
Trajectory optimization oﬀers mature tools for motion planning in high-dimensional spaces under dynamic constraints. However, when facing complex conﬁguration spaces, cluttered with obstacles, roboticists typically fall back to sampling-based planners that struggle in very high dimensions and with continuous diﬀerential constraints. Indeed, obstacles are the source of many textbook examples of problematic nonconvexities in the trajectory-optimization problem. Here we show that convex optimization can, in fact, be used to reliably plan trajectories around obstacles. Speciﬁcally, we consider planning problems with collision-avoidance constraints, as well as cost penalties and hard constraints on the shape, the duration, and the velocity of the trajectory. Combining the properties of B´ezier 

## Relevance to your work
This is the GCS motion planner a layered locomotion/navigation stack cites for globally-optimal, obstacle-aware trajectory generation with optimality certificates — the high-level planning layer above the tracking controller in work like [[@csomayshanklin2025dynamically]].

## Concepts


## Source
- Cited by [[@csomayshanklin2025dynamically]]
- bibkeys: `marcucci_motion_2022`
- arXiv: https://arxiv.org/abs/2205.04422
- URL: http://arxiv.org/abs/2205.04422
