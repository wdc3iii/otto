---
type: paper
citekey: reeds1990optimal
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Reeds, James A.
- Shepp, L. A.
year: 1990
venue: Pacific Journal of Mathematics
doi: 10.2140/pjm.1990.145.367
arxiv: null
url: https://doi.org/10.2140/pjm.1990.145.367
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@reeds1990optimal.pdf
bibkeys:
- reeds_optimal_1990
---

# Optimal paths for a car that goes both forwards and backwards.

> [!info] Reeds, James A.; Shepp, L. A. · 1990 · Pacific Journal of Mathematics

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Characterizes the shortest path (the "Reeds-Shepp curves") for a car with a bounded minimum turning radius that may drive both forwards and backwards between two poses.
**Problem** — Given start and end positions and headings, what is the shortest path for a car with a lower bound on radius of curvature, allowing reversals (cusps where it shifts into/out of reverse)?
**Method** — The authors show one need only consider paths with at most two cusps/reversals, and give a small sufficient family (at most 68 candidate paths, usually far fewer) of explicit-formula paths of the form CCSCC — arcs C of the minimum-turning-radius circle and straight segments S fitting smoothly, with some pieces possibly vanishing and reversals allowed. Computing each candidate's length and taking the minimum yields a simple shortest-path algorithm.
**Key results** — An explicit, finite closed-form enumeration of optimal geodesics for the forwards-and-backwards car. This extends Dubins (1957), who solved the no-reversal case where CSC and CCC paths suffice.

## Takeaways
- Foundational result in nonholonomic motion planning: the reversing car's shortest paths are a finite closed-form family, making the local steering problem exactly solvable.
- Reeds-Shepp curves are the standard steering primitive / local connector inside sampling-based planners (RRT/PRM) for car-like and other nonholonomic systems.
- Assumes a kinematic car with bounded curvature and no obstacles — it solves the two-point boundary-value steering problem, not global collision avoidance.

## Relevance to your work
The canonical optimal-steering result for nonholonomic vehicles, cited by [[@csomayshanklin2025dynamically]] as a classical baseline for dynamically feasible local connections that learned or reduced-order planners must reproduce or improve upon.

## Abstract (from bib)
The path taken by a car with a given minimum turning radius has a lower bound on its radius of curvature at ea

## Concepts


## Source
- Cited by [[@csomayshanklin2025dynamically]]
- bibkeys: `reeds_optimal_1990`
- DOI: https://doi.org/10.2140/pjm.1990.145.367
- URL: https://www.scinapse.io/papers/1971998222
