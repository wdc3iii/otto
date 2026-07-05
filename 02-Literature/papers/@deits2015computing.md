---
type: paper
citekey: deits2015computing
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Deits, Robin
- Tedrake, Russ
year: 2015
venue: Algorithmic Foundations of Robotics XI
doi: 10.1007/978-3-319-16595-0_7
arxiv: null
url: https://link.springer.com/10.1007/978-3-319-16595-0_7
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- akin_computing_2015
---

# Computing Large Convex Regions of Obstacle-Free Space Through Semidefinite Programming

> [!info] Deits, Robin; Tedrake, Russ · 2015 · Algorithmic Foundations of Robotics XI

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — IRIS (Iterative Regional Inflation by Semidefinite programming) quickly computes large convex polytopic/ellipsoidal regions of obstacle-free space via a sequence of convex optimizations.
**Problem** — Optimizing an objective over collision-free configurations (e.g. footstep or manipulator placement) is hard because free space is non-convex; a large certified convex free region turns the downstream problem convex.
**Method** — Alternates two convex programs: (1) a QP that finds separating hyperplanes carving a convex region away from the obstacles, and (2) an SDP that inscribes a maximum-volume ellipsoid in the resulting polytope. Hyperplanes and ellipsoid are refined over iterations to monotonically grow the region.
**Key results** — Produces large obstacle-free convex regions efficiently; the regions serve as convex constraints for downstream trajectory/placement optimization (from the abstract).

## Takeaways
- Converts non-convex free-space membership into a small set of linear (half-space) constraints — directly usable inside a QP/MIQP.
- Convex certificate of free space is a building block for footstep planning and safe corridors, not a planner itself.
- Monotone growth via alternating QP/SDP; seed-point dependent, so region placement matters.

## Relevance to your work
IRIS regions are the workhorse convex free-space certificates that layered locomotion planners build on; they let a footstep or reduced-order planner such as in [[@csomayshanklin2025dynamically]] pose collision-free reasoning as convex constraints.

## Abstract (from bib)
This paper presents iris (Iterative Regional Inﬂation by Semideﬁnite programming), a new method for quickly computing large polytopic and ellipsoidal regions of obstacle-free space through a series of convex optimizations. These regions can be used, for example, to eﬃciently optimize an objective over collision-free positions in space for a robot manipulator. The algorithm alternates between two convex optimizations: (1) a quadratic program that generates a set of hyperplanes to separate a convex region of space from the set of obstacles and (2) a semideﬁnite program that ﬁnds a maximum-volume ellipsoid inside the polytope intersection of the obstacle-free half-spaces deﬁned by those hyperplanes. Both the hyperplanes and the ellipsoid are reﬁned over several iterations to monotonically inc

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@csomayshanklin2025dynamically]]
- bibkeys: `akin_computing_2015`
- DOI: https://doi.org/10.1007/978-3-319-16595-0_7
- URL: https://link.springer.com/10.1007/978-3-319-16595-0_7
