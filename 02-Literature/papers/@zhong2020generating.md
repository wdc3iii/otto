---
type: paper
citekey: zhong2020generating
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Xingguang Zhong
- Yuwei Wu
- Dong Wang
- Qianhao Wang
- Chao Xu
- Fei Gao
year: 2020
venue: null
doi: null
arxiv: '2010.08744'
url: https://arxiv.org/abs/2010.08744
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@zhong2020generating.pdf
bibkeys:
- zhong2020generatinglargeconvexpolytopes
---

# Generating Large Convex Polytopes Directly on Point Clouds

> [!info] Xingguang Zhong; Yuwei Wu; Dong Wang; Qianhao Wang; Chao Xu; Fei Gao · 2020 · —

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A method to carve large, guaranteed-convex, obstacle-free polytopes directly out of raw point clouds in milliseconds, suitable for embedded platforms.
**Problem** — Convex free-space regions are the workhorse constraint representation for safe trajectory optimization, but generating them from cluttered point-cloud data is typically expensive and does not scale to onboard, real-time use.
**Method** — The core primitive is *sphere flipping*, a one-to-one invertible nonlinear map that transforms unordered points into a space where a collision-free star-convex polytope can be extracted. Exploiting star convexity, the polytope is then efficiently modified into a true convex polytope that is guaranteed obstacle-free.
**Key results** — Processes thousands of points within a few milliseconds and significantly outperforms state-of-the-art free-space generators in efficiency; demonstrated on 3D large-scale deformable topological mapping and quadrotor optimal trajectory planning.

## Takeaways
- Operates directly on point clouds — no meshing or occupancy-grid intermediary — which is what makes it embedded-friendly.
- The convex-polytope output is exactly the kind of safe-corridor constraint a downstream optimizer (e.g., an MPC or trajectory QP) consumes.
- Guarantees are geometric (collision-free convex region), not dynamic; feasibility of motion through the region is left to the planner.

## Relevance to your work
A hierarchical motion-planning stack needs a fast way to turn perception into convex free-space constraints for the high-level planner; this supplies that geometric layer beneath a [[@hierarchies2025motion]]-style architecture.

## Concepts


## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `zhong2020generatinglargeconvexpolytopes`
- arXiv: https://arxiv.org/abs/2010.08744
