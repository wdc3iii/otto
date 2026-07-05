---
type: paper
citekey: lee2010geometric
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- T. Lee
- M. Leoky
- N. H. McClamroch
year: 2010
venue: CDC
doi: 10.1109/CDC.2010.5717652
arxiv: null
url: https://doi.org/10.1109/CDC.2010.5717652
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- LeeCDC10
---

# Geometric tracking control of a quadrotor UAV on SE(3)

> [!info] T. Lee; M. Leoky; N. H. McClamroch · 2010 · CDC

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A nonlinear tracking controller developed intrinsically on SE(3) that drives a quadrotor to track position and heading with almost-global closed-loop stability.
**Problem** — A quadrotor is underactuated (four thrust inputs for six DOF), and coordinate-chart attitude representations (Euler angles) break down at large excursions, preventing globally valid tracking guarantees.
**Method** — The authors introduce a globally defined rigid-body model of the quadrotor and design a geometric tracking controller directly on the special Euclidean group SE(3), avoiding local parameterizations. The controller tracks four outputs — the center-of-mass position and the heading of one body-fixed axis — with provably almost-global closed-loop behavior.
**Key results** — Numerical examples show the controller recovering from aggressive initial conditions, including flipping upright from an initially upside-down attitude.

## Takeaways
- Working on SE(3) (rotation matrices, not Euler angles) removes singularities and yields almost-global rather than merely local tracking guarantees.
- Only four of six DOF can be independently commanded; the controller exploits the geometric structure of the underactuation rather than small-angle approximations.
- "Almost global" excludes a measure-zero set of antipodal attitude errors — a topological obstruction, not a design flaw.

## Relevance to your work
A canonical example of a geometric full-order tracking controller: the kind of high-fidelity inner loop that rides beneath a reduced-order or differentially-flat planning layer, which is exactly the layered structure safety-critical work like [[@cohen2025safety]] builds on.

## Concepts


## Source
- Cited by [[@cohen2025safety]]
- bibkeys: `LeeCDC10`
