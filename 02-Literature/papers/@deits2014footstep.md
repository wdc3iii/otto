---
type: paper
citekey: deits2014footstep
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Deits, Robin
- Tedrake, Russ
year: 2014
venue: 2014 IEEE-RAS International Conference on Humanoid Robots
doi: 10.1109/HUMANOIDS.2014.7041373
arxiv: null
url: https://doi.org/10.1109/HUMANOIDS.2014.7041373
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- deits_footstep_2014
---

# Footstep Planning on Uneven Terrain with Mixed-Integer Convex Optimization

> [!info] Deits, Robin; Tedrake, Russ · 2014 · 2014 IEEE-RAS International Conference on Humanoid Robots

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Casts footstep placement on uneven, obstacle-strewn terrain as a single mixed-integer convex program (MIQCQP) solvable to global optimum.
**Problem** — Footstep planning couples obstacle avoidance, kinematic reachability, and footstep rotation — constraints that are individually non-convex, making joint optimization hard.
**Method** — Formulates a mixed-integer quadratically-constrained quadratic program: reachability via a convex inner approximation of the foot's reachable space; footstep rotation via a piecewise-linear (never-overestimating) approximation of sine/cosine; obstacle avoidance by decomposing free space into convex safe regions and assigning each footstep to one via integer variables.
**Key results** — Demonstrated in 2D/3D and on humanoid-sensed environments; plans a few steps in under a second, or 10-30 footsteps in tens of seconds to minutes on a laptop. Implemented in the Drake MATLAB toolbox.

## Takeaways
- Turning reachability, rotation, and obstacle assignment into a single MIQCQP yields globally optimal footstep plans — a foundational convex-optimization footstep planner.
- The convex-safe-region decomposition (IRIS-style) and PWL rotation approximation are the enabling modeling tricks.
- Scales to only short horizons quickly; longer sequences cost seconds-to-minutes, so it is offline/receding-horizon rather than high-rate.

## Relevance to your work
The canonical mixed-integer convex footstep planner underpinning perception-driven walking on uneven terrain, cited by [[@dai2025walk]] as the planning layer for foothold-constrained locomotion.

## Abstract (from bib)
We present a new method for planning footstep placements for a robot walking on uneven terrain with obstacles, using a mixed-integer quadratically-constrained quadratic program (MIQCQP). Our approach is unique in that it handles obstacle avoidance, kinematic reachability, and rotation of footstep placements, which typically have required non-convex constraints, in a single mixed-integer optimization that can be efﬁciently solved to its global optimum. Reachability is enforced through a convex inner approximation of the reachable space for the robot’s feet. Rotation of the footsteps is handled by a piecewise linear approximation of sine and cosine, designed to ensure that the approximation never overestimates the robot’s reachability. Obstacle avoidance is ensured by decomposing the environ

## Concepts

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `deits_footstep_2014`
- DOI: https://doi.org/10.1109/HUMANOIDS.2014.7041373
