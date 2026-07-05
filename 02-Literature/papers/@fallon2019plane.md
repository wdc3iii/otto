---
type: paper
citekey: fallon2019plane
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Fallon, Maurice
- Antone, Matt
year: 2019
venue: \urlhttps://github.com/ori-drs/plane_seg
doi: null
arxiv: null
url: https://github.com/ori-drs/plane_seg
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- Fallon2019PlaneSeg
---

# Plane Seg – Robustly and Efficiently Extracting Contact Regions from Depth Data

> [!info] Fallon, Maurice; Antone, Matt · 2019 · \urlhttps://github.com/ori-drs/plane_seg

## Summary
> [!note] AI-drafted from the project (GitHub ori-drs/plane_seg) description — a base to refine; this is a software release, not a formal paper.

**TL;DR** — Plane Seg is an open-source library that robustly and efficiently fits planar contact regions to depth/LIDAR data and elevation maps for legged-robot footstep planning.

**Problem** — Perceptive locomotion needs steppable-surface geometry extracted online from noisy 3D sensing; extracting reliable planar contact regions quickly is the bottleneck.

**Method** — The core library (PCL-dependent) uses robust estimation to fit planes by clustering planar points with similar surface normals. A ROS wrapper (plane-seg-ros) ingests PointCloud2 and GridMap (elevation-map) inputs and outputs the extracted planar regions.

**Key results** — Provides a practical, real-time plane/contact-region segmentation utility widely reused in perceptive legged-locomotion pipelines (no formal benchmark reported here).

## Takeaways
- A tooling/software contribution (not a theory paper): normal-based clustering + robust plane fitting for contact-region extraction.
- Consumes both raw point clouds and elevation-map grids, making it a drop-in perception front-end for footstep planners.

## Relevance to your work
Supplies the steppable-region segmentation that perceptive footstep planners depend on; cited by [[@dai2025walk]] as the perception building block feeding terrain-aware foothold selection.

## Concepts


## Source
- Cited by [[@dai2025walk]]
- bibkeys: `Fallon2019PlaneSeg`
