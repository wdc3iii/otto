---
type: paper
citekey: meng2023terrainnet
tags: [navigation, method]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Meng, Xiangyun
- Hatch, Nathan
- Lambert, Alexander
- Li, Anqi
- Wagener, Nolan
- Schmittle, Matthew
- Lee, JoonHo
- Yuan, Wentao
- Chen, Zoey
- Deng, Samuel
- Okopal, Greg
- Fox, Dieter
- Boots, Byron
- Shaban, Amirreza
year: 2023
venue: arXiv
doi: 10.48550/arXiv.2303.15771
arxiv: '2303.15771'
url: http://arxiv.org/abs/2303.15771
zotero: null
summary: ai-draft
pdf: attachments/@meng2023terrainnet.pdf
status: to-read
mine: false
bibkeys:
- mengTerrainNetVisualModeling2023
---

# TerrainNet: Visual Modeling of Complex Terrain for High-speed, Off-road Navigation

> [!info] Xiangyun Meng; Nathan Hatch; Alexander Lambert; Anqi Li; Nolan Wagener; Matthew Schmittle; JoonHo Lee; Wentao Yuan; Zoey Chen; Samuel Deng; Greg Okopal; Dieter Fox; Byron Boots; Amirreza Shaban · 2023 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A camera-based terrain-perception network that predicts semantic and geometric terrain (for traversability) to support aggressive high-speed off-road navigation, integrated into a full autonomous-driving stack.
**Problem** — End-to-end scene prediction works on-road but hasn't transferred to complex outdoor terrain at high speed, where camera vision is essential but hard.
**Method** — TerrainNet: a multi-headed output representation capturing fine- and coarse-grained terrain features for traversability; accurate depth via self-supervised depth completion with multi-view RGB and stereo; efficient learned image-feature projections for real-time inference; trained on a large-scale real-world off-road dataset across diverse environments; supports costmap prediction for a planning module.
**Key results** — Extensive comparison against SOTA camera-only scene-prediction baselines, plus a real-world vehicle test integrating TerrainNet in a complete autonomous-driving stack on challenging off-road terrain (no numeric figures read).

## Takeaways
- Multi-headed semantic + geometric output captures both fine and coarse terrain features for traversability estimation.
- Self-supervised depth completion (multi-view RGB + stereo) yields accurate geometry from cameras alone.
- Designed for real-time costmap prediction feeding a downstream planner.

## Relevance to your work
Relevant to terrain-aware navigation and traversability estimation: a vision-only perception front end that turns imagery into semantic/geometric costmaps for a planner — the perception-to-cost pipeline is transferable to capability-aware navigation, though this targets a high-speed wheeled vehicle rather than a legged platform.

## Abstract (from bib)
Effective use of camera-based vision systems is essential for robust performance in autonomous off-road driving, particularly in the high-speed regime. Despite success in structured, on-road settings, current end-to-end approaches for scene prediction have yet to be successfully adapted for complex outdoor terrain. To this end, we present TerrainNet, a vision-based terrain perception system for semantic and geometric terrain prediction for aggressive, off-road navigation. The approach relies on several key insights and practical considerations for achieving reliable terrain modeling. The network includes a multi-headed output representation to capture fine- and coarse-grained terrain features necessary for estimating traversability. Accurate depth estimation is achieved using self-supervised depth completion with multi-view RGB and stereo inputs. Requirements for real-time performance and fast inference speeds are met using efficient, learned image feature projections. Furthermore, the model is trained on a large-scale, real-world off-road dataset collected across a variety of diverse outdoor environments. We show how TerrainNet can also be used for costmap prediction and provide a detailed framework for integration into a planning module. We demonstrate the performance of TerrainNet through extensive comparison to current state-of-the-art baselines for camera-only scene prediction. Finally, we showcase the effectiveness of integrating TerrainNet within a complete autonomous-driving stack by conducting a real-world vehicle test in a challenging off-road scenario.

## Concepts
- [[traversability-estimation]]

## Source
- bibkeys: `mengTerrainNetVisualModeling2023`
- arXiv: http://arxiv.org/abs/2303.15771
- DOI: https://doi.org/10.48550/arXiv.2303.15771
- URL: http://arxiv.org/abs/2303.15771
