---
type: paper
citekey: deits2015efficient
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Deits, Robin
- Tedrake, Russ
year: 2015
venue: 2015 IEEE International Conference on Robotics and Automation (ICRA)
doi: 10.1109/ICRA.2015.7138978
arxiv: null
url: https://doi.org/10.1109/ICRA.2015.7138978
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- deits_efficient_2015
---

# Efficient mixed-integer planning for UAVs in cluttered environments

> [!info] Deits, Robin; Tedrake, Russ · 2015 · 2015 IEEE International Conference on Robotics and Automation (ICRA)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.

**TL;DR** — Plans smooth, entirely collision-free quadrotor trajectories via a mixed-integer optimization that assigns polynomial segments to precomputed convex obstacle-free regions (from IRIS), with sums-of-squares constraints guaranteeing the whole continuous trajectory avoids obstacles.

**Problem** — Obstacle avoidance is inherently non-convex; prior methods defined convex regions from the obstacle faces (yielding many integer variables) and enforced avoidance only at a finite set of sample/knot points, so collisions could occur between samples.

**Method** — Uses IRIS greedy convex segmentation to pre-compute convex regions of free space, then a mixed-integer optimization assigns polynomial trajectories to those regions; because there are far fewer regions than obstacle faces, the number of integer variables drops sharply and the problem solves to global optimum faster. A sums-of-squares (SOS) programming technique certifies the entire piecewise-polynomial trajectory is collision-free using convex constraints.

**Key results** — Demonstrated in 2D and 3D using a dynamical quadrotor model in the Drake toolbox, remaining tractable even for tens or hundreds of obstacle faces.

## Abstract (from bib)
We present a new approach to the design of smooth trajectories for quadrotor unmanned aerial vehicles (UAVs), which are free of collisions with obstacles along their entire length. To avoid the non-convex constraints normally required for obstacle-avoidance, we perform a mixed-integer optimization in which polynomial trajectories are assigned to convex regions which are known to be obstacle-free. Prior approaches have used the faces of the obstacles themselves to deﬁne these convex regions. We instead use IRIS, a recently developed technique for greedy convex segmentation [1], to pre-compute convex regions of safe space. This results in a substantially reduced number of integer variables, which improves the speed with which the optimization can be solved to its global optimum, even for ten

## Takeaways
- The key idea is decoupling: precompute convex free-space regions once (IRIS), then let the MIP only decide region assignment — this is what collapses the integer-variable count and gives fast global solves.
- SOS certification upgrades collision-avoidance from "safe at knot points" to "safe over the entire continuous trajectory" via convex constraints — a rigorous continuous-time guarantee.
- Seminal reference for convex-decomposition + mixed-integer trajectory planning in clutter (UAV context), a template later carried into legged/dynamic settings.

## Relevance to your work
Foundational method for dynamically-feasible, collision-free planning in cluttered spaces via convex free-space decomposition — the lineage behind reachable-polytope planners for legged robots; see [[@csomayshanklin2025dynamically]].

## Concepts


## Source
- Cited by [[@csomayshanklin2025dynamically]], [[@hierarchies2025motion]]
- bibkeys: `deits_efficient_2015`
- DOI: https://doi.org/10.1109/ICRA.2015.7138978
