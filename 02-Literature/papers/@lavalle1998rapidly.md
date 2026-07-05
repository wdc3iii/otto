---
type: paper
citekey: lavalle1998rapidly
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- LaValle, Steven M.
year: 1998
venue: The annual research report
doi: null
arxiv: null
url: https://msl.cs.illinois.edu/~lavalle/papers/Lav98c.pdf
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- lavalle1998rapidlyexploring
---

# Rapidly-Exploring Random Trees : A New Tool for Path Planning

> [!info] LaValle, Steven M. · 1998 · The annual research report

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces the Rapidly-exploring Random Tree (RRT), a randomized incremental data structure for path planning that handles high-DOF systems with nonholonomic and dynamic constraints.
**Problem** — Existing randomized planners (e.g., probabilistic roadmaps) rely on point-to-point steering and are awkward for problems with differential/nonholonomic constraints and dynamics.
**Method** — An RRT is grown incrementally: at each iteration a random sample is drawn in the state space and the tree is extended from its nearest node by applying a control input that drives the system slightly toward the sample. This biases exploration toward unexplored regions ("Voronoi bias") without requiring exact connections, so the tree rapidly and uniformly covers the space.
**Key results** — Demonstrates RRTs on holonomic, nonholonomic, and kinodynamic problems of up to twelve degrees of freedom, establishing several favorable exploration properties and a simple implementation.

## Takeaways
- The Voronoi-biased expansion is what makes RRTs explore efficiently; nearest-neighbor selection is the computational core.
- Naturally accommodates dynamics/nonholonomic constraints by planning in state space via forward integration of control inputs — no need for a steering solver.
- Foundational, single-query sampling-based planner; basic form is not asymptotically optimal (that came later with RRT*).

## Relevance to your work
The canonical sampling-based planner cited as the global/geometric layer that a reduced-order or reachability-based motion planner refines; see [[@csomayshanklin2025dynamically]], which uses tractable tube/reachable-set planning where RRT would otherwise search the raw state space.

## Concepts

## Source
- Cited by [[@csomayshanklin2025dynamically]], [[@hierarchies2025motion]]
- bibkeys: `lavalle1998rapidlyexploring`
