---
type: paper
citekey: shkolnik2009reachability
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Shkolnik, Alexander
- Walter, Matthew
- Tedrake, Russ
year: 2009
venue: 2009 IEEE International Conference on Robotics and Automation
doi: 10.1109/ROBOT.2009.5152874
arxiv: null
url: null
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- shkolnik_reachability-guided_2009
- voronoi
---

# Reachability-guided sampling for planning under differential constraints

> [!info] Shkolnik, Alexander; Walter, Matthew; Tedrake, Russ · 2009 · 2009 IEEE International Conference on Robotics and Automation

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A reachability-guided sampling strategy for RRTs that biases tree expansion using an estimated feasibility (reachability) set, dramatically improving performance on severely differentially-constrained systems.
**Problem** — RRTs scale to large planning problems but their efficiency collapses under kinodynamic/differential constraints: obstacle fields with narrow tunnels or "tubes" and dynamically constrained systems cause the tree to grow inefficiently at its boundaries.
**Method** — A new RRT sampling strategy driven by an estimated feasibility set (reachability), so nodes are chosen and extended toward reachable regions rather than by naive nearest-neighbor Euclidean sampling. This concentrates growth where the system can actually move given its dynamics.
**Key results** — Demonstrates a dramatic improvement on severely constrained systems, illustrated in detail on a pendulum swing-up task and on path planning for a nonholonomic car.

## Takeaways
- The key insight is replacing a metric that ignores dynamics with a reachability-informed one, fixing the well-known failure mode of RRTs at feasibility boundaries.
- Especially effective in "tube"-like narrow feasible regions — directly relevant to constrained corridors in state space.
- Motivating examples (swing-up, nonholonomic car) show it targets underactuated / nonholonomic dynamics, not just geometric planning.

## Relevance to your work
A classical kinodynamic sampling-based planning technique, cited by [[@csomayshanklin2025dynamically]] for how reachability structure guides dynamically feasible planning — conceptually adjacent to reasoning about where a reduced-order model can actually be driven.

## Abstract (from bib)
Rapidly-exploring random trees (RRTs) are widely used to solve large planning problems where the scope prohibits the feasibility of deterministic solvers, but the efficiency of these algorithms can be severely compromised in the presence of certain kinodynamics constraints. Obstacle fields with tunnels, or tubes are notoriously difficult, as are systems with differential constraints, because the tree grows inefficiently at the boundaries. Here we present a new sampling strategy for the RRT algorithm, based on an estimated feasibility set, which affords a dramatic improvement in performance in these severely constrained systems. We demonstrate the algorithm with a detailed look at the expansion of an RRT in a swing up task, and on path planning for a nonholonomic car.

## Concepts


## Source
- Cited by [[@csomayshanklin2025dynamically]]
- bibkeys: `shkolnik_reachability-guided_2009`, `voronoi`
- DOI: https://doi.org/10.1109/ROBOT.2009.5152874
