---
type: paper
citekey: herbert2017fastrack
tags: [control, planning, navigation]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Herbert, Sylvia L.
- Chen, Mo
- Han, SooJean
- Bansal, Somil
- Fisac, Jaime F.
- Tomlin, Claire J.
year: 2017
venue: '2017 IEEE 56th Annual Conference on Decision and Control (CDC)'
doi: 10.1109/CDC.2017.8263867
arxiv: '1703.07373'
url: http://arxiv.org/abs/1703.07373
zotero: null
summary: ai-draft
pdf: attachments/@herbert2017fastrack.pdf
status: to-read
mine: false
bibkeys:
- herbertFaSTrackModularFramework2017
---

# FaSTrack: A Modular Framework for Fast and Guaranteed Safe Motion Planning

> [!info] Sylvia L. Herbert; Mo Chen; SooJean Han; Somil Bansal; Jaime F. Fisac; Claire J. Tomlin · 2017 · 2017 IEEE 56th Annual Conference on Decision and Control (CDC)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — FaSTrack lets a fast planner use simplified dynamics while a precomputed safety controller guarantees a tracking-error bound capturing all deviations due to high-dimensional dynamics and disturbances.
**Problem** — Trajectory planning through unknown cluttered environments is computationally intensive; simplified dynamics plan fast but sacrifice safety/feasibility, while sophisticated models are safe but too slow for real-time planning.
**Method** — Pair a path/trajectory planner using simplified dynamics with a safety controller derived for the true high-dimensional system; the framework provides a guaranteed tracking-error bound that captures all possible deviations from high-dimensional dynamics and external disturbances. Modular — compatible with most existing planners.
**Key results** — Demonstrated with a 10D nonlinear quadrotor model tracking a 3D path from an RRT planner (no numeric figures read).

## Takeaways
- Decouples planning (simple model, fast) from tracking (full model, safe) and bridges them with a provable tracking-error bound — a "tube" the planner must respect.
- The bound is precomputed (Hamilton-Jacobi pursuit-evasion between planner and tracker), so online cost is just the fast planner plus a lookup-based safety controller.
- Modular: drops in around most existing path/trajectory planners.

## Relevance to your work
Core reference for your tube-MPC / tracking-error-bound line: FaSTrack is the canonical formalization of a guaranteed tracking-error bound between a reduced-order planning model and full dynamics — directly analogous to the dynamic-tube / reduced-order-model constructions you use for legged navigation.

## Abstract (from bib)
Fast and safe navigation of dynamical systems through a priori unknown cluttered environments is vital to many applications of autonomous systems. However, trajectory planning for autonomous systems is computationally intensive, often requiring simplified dynamics that sacrifice safety and dynamic feasibility in order to plan efficiently. Conversely, safe trajectories can be computed using more sophisticated dynamic models, but this is typically too slow to be used for real-time planning. We propose a new algorithm FaSTrack: Fast and Safe Tracking for High Dimensional systems. A path or trajectory planner using simplified dynamics to plan quickly can be incorporated into the FaSTrack framework, which provides a safety controller for the vehicle along with a guaranteed tracking error bound. This bound captures all possible deviations due to high dimensional dynamics and external disturbances. Note that FaSTrack is modular and can be used with most current path or trajectory planners. We demonstrate this framework using a 10D nonlinear quadrotor model tracking a 3D path obtained from an RRT planner.

## Concepts
- [[tracking-error-bound]]
- [[reduced-order-model]]
- [[dynamic-tube]]

## Source
- bibkeys: `herbertFaSTrackModularFramework2017`
- arXiv: http://arxiv.org/abs/1703.07373
- DOI: https://doi.org/10.1109/CDC.2017.8263867
- URL: http://arxiv.org/abs/1703.07373
