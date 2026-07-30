---
type: paper
citekey: shi2026oneocc
tags: [navigation, locomotion]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Shi, Hao
- Wang, Ze
- Guo, Shangwei
- Duan, Mengfei
- Wang, Song
- Chen, Teng
- Yang, Kailun
- Wang, Lin
- Wang, Kaiwei
year: 2025
venue: CVPR 2026
doi: 10.48550/arXiv.2511.03571
arxiv: '2511.03571'
url: https://arxiv.org/abs/2511.03571
pdf: attachments/@shi2026oneocc.pdf
zotero: null
status: to-read
mine: false
---

# OneOcc: Semantic Occupancy Prediction for Legged Robots with a Single Panoramic Camera

> [!info] Hao Shi; Ze Wang; Shangwei Guo; Mengfei Duan; Song Wang; Teng Chen; Kailun Yang; Lin Wang; Kaiwei Wang · 2025 · CVPR 2026
> arXiv:2511.03571 (2511.03571v2, 2026-03-15) · Accepted to CVPR 2026. Datasets and code will be publicly available at https://github.com/MasterHow/OneOcc

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.2 (ref `[12]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[12]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Map / geometry / potential-field anticipation as supervised learning*. Occupancy prediction as a standalone perception problem, specifically for **legged** robots.

## Your take (your words — authoritative, not ai-draft)
> **Take:** the modern framing of proposals #1+#2 as a standalone perception problem — useful as an upper bound on what an aux head could be expected to represent.

## Abstract (from arXiv)
Robust 3D semantic occupancy is crucial for legged/humanoid robots, yet most semantic scene
completion (SSC) systems target wheeled platforms with forward-facing sensors. We present OneOcc, a
vision-only panoramic SSC framework designed for gait-introduced body jitter and 360° continuity.
OneOcc combines: (i) Dual-Projection fusion (DP-ER) to exploit the annular panorama and its
equirectangular unfolding, preserving 360° continuity and grid alignment; (ii) Bi-Grid Voxelization
(BGV) to reason in Cartesian and cylindrical-polar spaces, reducing discretization bias and
sharpening free/occupied boundaries; (iii) a lightweight decoder with Hierarchical AMoE-3D for
dynamic multi-scale fusion and better long-range/occlusion reasoning; and (iv) plug-and-play Gait
Displacement Compensation (GDC) learning feature-level motion correction without extra sensors. We
also release two panoramic occupancy benchmarks: QuadOcc (real quadruped, first-person 360°) and
Human360Occ (H3O) (CARLA human-ego 360° with RGB, Depth, semantic occupancy; standardized
within-/cross-city splits). OneOcc sets a new state of the art on QuadOcc, outperforming strong
vision baselines and remaining competitive with classical LiDAR baselines; on H3O it gains +3.83
mIoU (within-city) and +8.08 (cross-city). Modules are lightweight, enabling deployable
full-surround perception for legged/humanoid robots. Datasets and code will be publicly available at
https://github.com/MasterHow/OneOcc.

## Concepts
- [[occupancy-anticipation]]
- [[traversability-estimation]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/2511.03571 (2511.03571v2, published 2025-11-05, updated 2026-03-15)
- DOI: https://doi.org/10.48550/arXiv.2511.03571
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.2.
