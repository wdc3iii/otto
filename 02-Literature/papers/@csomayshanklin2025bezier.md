---
type: paper
citekey: csomayshanklin2025bezier
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Csomay-Shanklin, Noel
- Ames, Aaron D
year: 2025
venue: 2025 American Control Conference (ACC)
doi: null
arxiv: '2411.13506'
url: https://arxiv.org/abs/2411.13506
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@csomayshanklin2025bezier.pdf
bibkeys:
- csomay2024bezier
---

# Bezier reachable polytopes: Efficient certificates for robust motion planning with layered architectures

> [!info] Csomay-Shanklin, Noel; Ames, Aaron D · 2025 · 2025 American Control Conference (ACC)
> [!info]- otto authors: [[aaron-ames]] · [[noel-csomay-shanklin]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — Introduces Bézier Reachable Polytopes: polytopic certificates of which reference trajectories a low-level tracking controller can actually follow under state/input constraints, giving layered planner–tracker architectures a tractable feasibility guarantee.

**Problem** — Control architectures are built as independently designed layers, but providing end-to-end guarantees requires reasoning about each layer's capabilities and their interconnections jointly at design time — hard to do tractably, especially for nonlinear systems.

**Method** — Works in the space of Bézier polynomial reference trajectories and exploits the geometric (convex-hull) properties of Bézier curves to represent the set of trackable, constraint-satisfying trajectories as an efficient polytope — expressible as a linear inequality in Bézier coefficient space. This certificate connects a planner–tracker pair to a high-level decision-making layer while preserving feasibility.

**Key results** — Demonstrates that the polytopic certificate lets long-horizon tasks over layered architectures be reasoned about in a computationally tractable manner (ACC 2025).

## Takeaways
- The polytopic certificate lives in Bézier coefficient space, so planner-side feasibility becomes a linear inequality — cheap enough to embed in a high-level planner.
- Encodes what the tracker can achieve (a tracking-error / reachability certificate) as the interface between layers — the crux of feasibility-guaranteed layered control.
- Limitation: relies on Bézier parameterization of references and on being able to certify the tracker's reachable set; scaling/tightness for general nonlinear trackers is where the difficulty concentrates.

## Relevance to your work
Directly relevant to layered planning–tracking control for legged systems: it makes the tracker's achievable set a first-class, planner-usable object — see [[@hierarchies2025motion]].

## Concepts
[[hierarchical-control]] · [[tracking-error-bound]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `csomay2024bezier`
