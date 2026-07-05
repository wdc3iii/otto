---
type: paper
citekey: segal2009generalized
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- A. Segal
- D. Haehnel
- S. Thrun
year: 2009
venue: 'Proceedings of Robotics: Science and Systems'
doi: 10.15607/RSS.2009.V.021
arxiv: null
url: https://doi.org/10.15607/RSS.2009.V.021
zotero: null
summary: ai-draft
pdf: attachments/@segal2009generalized.pdf
status: to-read
mine: false
bibkeys:
- segal2009generalized
---

# Generalized-ICP

> [!info] A. Segal; D. Haehnel; S. Thrun · 2009 · Proceedings of Robotics: Science and Systems

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Generalized-ICP unifies point-to-point and point-to-plane ICP in a single probabilistic (plane-to-plane) framework that models locally planar surface structure in *both* scans.
**Problem** — Standard ICP variants use ad hoc correspondence weighting and are sensitive to the maximum match-distance parameter; point-to-plane only exploits surface structure in the model scan.
**Method** — Casts registration as MLE with per-point covariances derived from local surface geometry, so both scans contribute planar structure ("plane-to-plane"). This keeps ICP's speed and simplicity while admitting richer probabilistic terms (outliers, measurement noise).
**Key results** — On simulated and real-world scans it outperforms standard ICP and point-to-plane ICP, and is more robust to incorrect correspondences, making the match-distance parameter easier to tune.

## Takeaways
- The covariance-weighted MLE formulation is the durable idea: it downweights correspondences along low-information directions rather than rejecting them outright.
- Retains ICP's computational profile, so it drops into existing registration pipelines with minimal cost.
- Assumes locally planar surfaces and reasonable initialization; still a local optimizer, so it inherits ICP's basin-of-attraction limits.

## Relevance to your work
A perception-consistency pipeline for legged terrain mapping (e.g. [[@terrain2026consistent]]) relies on robust scan/point-cloud registration to align successive depth frames into a coherent elevation map; GICP is a standard, robust building block for that alignment.

## Concepts


## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `segal2009generalized`
- DOI: https://doi.org/10.15607/RSS.2009.V.021
