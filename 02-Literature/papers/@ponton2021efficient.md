---
type: paper
citekey: ponton2021efficient
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Ponton, Brahayam
- Khadiv, Majid
- Meduri, Avadesh
- Righetti, Ludovic
year: 2021
venue: IEEE Transactions on Robotics
doi: 10.1109/TRO.2020.3048125
arxiv: null
url: https://doi.org/10.1109/TRO.2020.3048125
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- ponton_efficient_2021
---

# Efficient Multicontact Pattern Generation With Sequential Convex Approximations of the Centroidal Dynamics

> [!info] Ponton, Brahayam; Khadiv, Majid; Meduri, Avadesh; Righetti, Ludovic · 2021 · IEEE Transactions on Robotics

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A convex relaxation of the centroidal dynamics that generates physically consistent multicontact behaviors efficiently via iterated second-order cone programs, jointly optimizing trajectories, contact forces, and motion timing.
**Problem** — Computing physically consistent multicontact behaviors is expensive; even the decomposed kinematic/centroidal formulation remains hard to solve fast enough for online use.
**Method** — A general convex relaxation of the centroidal dynamics yields two algorithms based on iterative second-order cone programs that optimize centroidal trajectories, contact forces, and — importantly — motion timing. The relaxation is embedded in a kinodynamic method for full-body motion and, via a mixed-integer solver, to find dynamically consistent contact sequences.
**Key results** — Extensive numerical experiments show high computational efficiency (suggesting use in a fast receding-horizon loop); planned motions were executed on simulated humanoids and quadrupeds and on a real quadruped.

## Takeaways
- Convexifying the centroidal dynamics via SOCPs is the core contribution — it makes timing optimization tractable alongside forces and trajectories.
- The relaxation slots into both kinodynamic full-body generation and mixed-integer contact-sequence search, spanning planning granularities.
- Fast enough to suggest receding-horizon (MPC-style) deployment; demonstrated on real quadruped hardware.

## Abstract (from bib)
This article investigates the problem of efficient computation of physically consistent multicontact behaviors. Recent work showed that under mild assumptions, the problem could be decomposed into simpler kinematic and centroidal dynamic optimization problems. Based on this approach, we propose a general convex relaxation of the centroidal dynamics leading to two computationally efficient algorithms based on iterative resolutions of second-order cone programs. They optimize centroidal trajectories, contact forces, and importantly the timing of the motions. We include the approach in a kinodynamic optimization method to generate full-body movements. Finally, the approach is embedded in a mixed-integer solver to further find dynamically consistent contact sequences. Extensive numerical exper

## Relevance to your work
Cited for efficient reduced-order (centroidal) multicontact pattern generation with convex relaxations — a building block for the planning hierarchy in [[@hierarchies2025motion]].

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `ponton_efficient_2021`
- DOI: https://doi.org/10.1109/TRO.2020.3048125
