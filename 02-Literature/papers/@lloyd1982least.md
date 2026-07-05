---
type: paper
citekey: lloyd1982least
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Lloyd, Stuart
year: 1982
venue: IEEE transactions on information theory
doi: 10.1109/TIT.1982.1056489
arxiv: null
url: https://doi.org/10.1109/TIT.1982.1056489
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- lloyd1982least
---

# Least squares quantization in PCM

> [!info] Lloyd, Stuart · 1982 · IEEE transactions on information theory

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Derives the necessary conditions for a minimum-distortion scalar quantizer with a finite number of levels, giving the classic iterative "Lloyd" procedure that underlies k-means clustering.
**Problem** — In PCM, quantum levels should be spaced more densely where the signal amplitude is more likely; prior work (Panter–Dite) only gave the asymptotic density as the number of levels grows large.
**Method** — For any finite number of quanta, the paper derives necessary optimality conditions the quantization levels and their intervals must satisfy under a minimum average quantization-noise-power (mean-squared error) criterion — the centroid condition (each level is the conditional mean of its cell) and nearest-neighbor cell boundaries. These conditions are solved iteratively.
**Key results** — Shows the finite result recovers the Panter–Dite asymptotic density as levels grow; tabulates optimum quantizers for 2^b levels, b = 1..7, for Gaussian and Laplacian signal distributions.

## Takeaways
- Source of the centroid + nearest-neighbor optimality conditions and the alternating "Lloyd's algorithm," i.e., the 1-D / MSE ancestor of k-means (Lloyd–Max quantization).
- The optimal quantizer balances two coupled conditions; alternating between them monotonically decreases distortion but only guarantees a local optimum.
- A foundational information-theory result far outside robotics, cited for its clustering/quantization algorithm rather than PCM.

## Relevance to your work
Cited as the algorithmic basis for k-means-style clustering — e.g., partitioning free space, waypoints, or convex regions when building the graph/region abstractions a hierarchical motion planner like [[@hierarchies2025motion]] searches over.

## Concepts

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `lloyd1982least`
