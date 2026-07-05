---
type: paper
citekey: marcucci2023motion
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Marcucci, Tobia
- Petersen, Mark
- von Wrangel, David
- Tedrake, Russ
year: 2023
venue: Science robotics
doi: 10.1126/scirobotics.adf7843
arxiv: 2205.04422
url: https://arxiv.org/abs/2205.04422
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@marcucci2023motion.pdf
bibkeys:
- marcucci_motion_2022
---

# Motion planning around obstacles with convex optimization

> [!info] Marcucci, Tobia; Petersen, Mark; von Wrangel, David; Tedrake, Russ · 2023 · Science robotics

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Shows that convex optimization can reliably plan smooth, collision-free trajectories through cluttered spaces, via a tight mixed-integer formulation (GCS) whose relaxation usually yields globally-optimal paths after cheap rounding.
**Problem** — Trajectory optimization is strong in high dimensions under dynamics, but obstacles introduce textbook nonconvexities, so practitioners fall back to sampling-based planners that scale poorly in high dimensions with continuous differential constraints.
**Method** — Combine Bézier-curve trajectory parameterizations with the Graphs of Convex Sets (GCS) shortest-path framework to write planning as a compact mixed-integer program handling collision avoidance plus costs/constraints on shape, duration, and velocity. The convex relaxation is very tight, so cheap rounding typically recovers globally-optimal trajectories, reducing the MIP back to a convex program and yielding optimality bounds.
**Key results** — Demonstrated on a quadrotor flying through buildings and a 14-DOF dual-arm manipulator in confined space; on a 7-DOF arm, GCS finds higher-quality trajectories in less time than widely-used sampling-based planners.

## Takeaways
- Reframes obstacle avoidance as a shortest-path problem over convex sets, turning a hard nonconvex MIP into a near-convex problem with certificates of optimality.
- Bézier parameterization gives closed-form control over continuity, duration, and velocity bounds.
- Scales to high DOF where sampling planners degrade; the more general framework behind the axis-aligned-box specialization ([[@marcucci2024fast]]).

## Relevance to your work
A globally-optimal, constraint-aware trajectory planner attractive as the geometric/global layer for legged navigation; pairs with reduced-order and safe-corridor methods in hierarchical planners such as [[@hierarchies2025motion]] that must route a template through cluttered, safe convex regions.

## Concepts

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `marcucci_motion_2022`
