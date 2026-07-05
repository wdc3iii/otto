---
type: paper
citekey: csomayshanklin2024dynamically
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Noel Csomay-Shanklin
- William D. Compton
- Aaron D. Ames
year: 2024
venue: null
doi: null
arxiv: '2411.13507'
url: https://arxiv.org/abs/2411.13507
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@csomayshanklin2024dynamically.pdf
bibkeys:
- csomayshanklin2024dynamicallyfeasiblepathplanning
---

# Dynamically Feasible Path Planning in Cluttered Environments via Reachable Bezier Polytopes

> [!info] Noel Csomay-Shanklin; William D. Compton; Aaron D. Ames · 2024 · —

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — Uses reachable Bézier polytopes to plan paths through cluttered, non-convex environments that are simultaneously collision-free and dynamically feasible, with GPU offloading to hit real-time rates.

**Problem** — Deploying robots in the real world requires quickly producing paths through cluttered, non-convex spaces that are both kinematically feasible (collision-free) and dynamically feasible (consistent with the system's dynamics) — so both free space and dynamics must be handled during planning.

**Method** — Applies reachable Bézier polytopes as an efficient tool for generating trajectories that satisfy both kinematic and dynamic requirements, within a layered control architecture; offloads specific computations to the GPU so the algorithm meets tight real-time requirements for nonlinear control systems.

**Key results** — Demonstrated on the task of 3D hopping in a cluttered environment, producing collision-free, dynamically feasible paths in real time.

## Takeaways
- Reachable Bézier polytopes fold dynamic feasibility into the geometric planning stage, so the planner never proposes a path the low-level controller can't track.
- GPU offloading is what makes the polytope-based feasibility check real-time — an implementation choice central to the contribution.
- Validated on underactuated 3D hopping, i.e. genuinely dynamic (not quasi-static) locomotion in clutter.

## Relevance to your work
A concrete instance of dynamically-feasible layered planning for legged locomotion — the applied companion to reachable-polytope certificate theory; see [[@hierarchies2025motion]].

## Concepts
[[hierarchical-control]] · [[tracking-error-bound]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `csomayshanklin2024dynamicallyfeasiblepathplanning`
- arXiv: https://arxiv.org/abs/2411.13507
