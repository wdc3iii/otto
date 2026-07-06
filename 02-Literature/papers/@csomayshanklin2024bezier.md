---
type: paper
citekey: csomayshanklin2024bezier
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Noel Csomay-Shanklin
- Aaron D. Ames
year: 2024
venue: arXiv:2411.13506
doi: null
arxiv: '2411.13506'
url: https://arxiv.org/abs/2411.13506
zotero: null
summary: ai-draft
pdf: attachments/@csomayshanklin2024bezier.pdf
status: to-read
mine: false
bibkeys:
- future_acc
---

# Bezier Reachable Polytopes: Efficient Certificates for Robust Motion Planning with Layered Architectures

> [!info] Noel Csomay-Shanklin; Aaron D. Ames · 2024 · arXiv:2411.13506
> [!info]- otto authors: [[aaron-ames]] · [[noel-csomay-shanklin]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Introduces Bézier Reachable Polytopes: efficient polytopic certificates of which Bézier-polynomial reference trajectories a low-level controller can actually track under state and input constraints, enabling holistic guarantees for layered planner-tracker architectures.
**Problem** — Layered control stacks combine independently designed blocks (planner, tracker, high-level decision maker), but joint feasibility across layers is non-trivial and usually established ad hoc; guarantees require reasoning about each layer's capabilities and their interconnections at design time.
**Method** — Characterizes the set of Bézier reference trajectories trackable by the low-level controller while satisfying state/input constraints, and exploits the geometric (convex-hull / control-point) properties of Bézier polynomials to keep this reachable set as an efficient polytope. The resulting certificate connects a planner-tracker pair to a high-level decision layer while preserving feasibility.
**Key results** — Provides a constructive, computationally tractable certificate that lets long-horizon tasks be reasoned about at the trajectory-space level for layered architectures (from the abstract).

## Takeaways
- Reachability is posed in reference-trajectory space (Bézier control points), not full state space — that is what keeps it polytopic and cheap.
- Directly targets the layered planner/tracker joint-feasibility problem, turning tracking guarantees into constraints a high-level planner can respect.
- Bézier convex-hull property is the key enabler for an efficient polytopic representation.

## Relevance to your work
This is a precursor to the dynamically-feasible layered planning in [[@csomayshanklin2025dynamically]]: the Bézier reachable polytope is the certificate that ties a tracking-error-bounded low-level controller to a high-level planner, central to constructive layered-architecture guarantees.

## Concepts
[[hierarchical-control]] · [[tracking-error-bound]]

## Source
- Cited by [[@csomayshanklin2025dynamically]]
- bibkeys: `future_acc`
- arXiv: https://arxiv.org/abs/2411.13506
- URL: https://arxiv.org/abs/2411.13506
