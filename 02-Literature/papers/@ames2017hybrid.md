---
type: paper
citekey: ames2017hybrid
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Ames, Aaron D
- Poulakakis, Ioannis
year: 2017
venue: 'Bioinspired Legged Locomotion: Models, Concepts, Control and Applications'
doi: null
arxiv: null
url: http://ames.caltech.edu/HZD_bookchapter.pdf
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@ames2017hybrid.pdf
bibkeys:
- ames2017hybrid
---

# Hybrid zero dynamics control of legged robots

> [!info] Ames, Aaron D; Poulakakis, Ioannis · 2017 · Bioinspired Legged Locomotion: Models, Concepts, Control and Applications

## Summary
> [!note] AI-drafted from the chapter introduction — a base to refine.
**TL;DR** — A survey chapter on hybrid zero dynamics (HZD), the paradigm for designing feedback laws that induce provably stable dynamic walking and running on underactuated bipedal robots.
**Problem** — Legged robots are underactuated and hybrid (continuous swing phases punctuated by discrete impacts); designing controllers with analytically tractable stability guarantees for the resulting limit cycles is hard.
**Method** — HZD (originating with Grizzle, Westervelt, and collaborators) defines a set of holonomic virtual-constraint output functions and drives them to zero, rendering a lower-dimensional attractive, invariant surface. The restricted dynamics on that surface — the hybrid zero dynamics — govern the existence and stability of the periodic gait, reducing the stability question to a low-dimensional system.
**Key results** — Reviews the arc from the planar robot RABBIT (stable walking, attempted running) through compliant HZD on MABEL and Lyapunov-based HZD (CLF-QP) on DURUS-2D, spanning walking and running across underactuated and compliant platforms.

## Takeaways
- The zero-dynamics surface is a reduced-order model of the full hybrid robot: control the outputs, and stability collapses to a much lower-dimensional analysis.
- Lyapunov-based HZD recasts virtual-constraint tracking as a CLF-QP, giving flexibility to add constraints like torque saturation.
- Method is tailored to underactuated locomotion, distinct from full-actuation ZMP frameworks; compliance (springs/tendons) matters for running.

## Relevance to your work
HZD is the canonical way to embed a low-dimensional gait model in a high-DoF legged robot with formal stability, directly the layered/reduced-order-model perspective developed in [[@hierarchies2025motion]].

## Concepts
[[reduced-order-model]] · [[hierarchical-control]]

## Source
- Cited by [[@csomayshanklin2024robust]], [[@hierarchies2025motion]]
- bibkeys: `ames2017hybrid`
