---
type: paper
citekey: kong2023rethinking
tags: [navigation, method]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Kong, Lingdong
- Liu, Youquan
- Chen, Runnan
- Ma, Yuexin
- Zhu, Xinge
- Li, Yikang
- Hou, Yuenan
- Qiao, Yu
- Liu, Ziwei
year: 2023
venue: ICCV 2023 (RangeFormer)
doi: 10.48550/arXiv.2303.05367
arxiv: '2303.05367'
url: https://arxiv.org/abs/2303.05367
pdf: attachments/@kong2023rethinking.pdf
zotero: null
status: to-read
mine: false
---

# Rethinking Range View Representation for LiDAR Segmentation

> [!info] Lingdong Kong; Youquan Liu; Runnan Chen; Yuexin Ma; Xinge Zhu; Yikang Li; Yuenan Hou; Yu Qiao; Ziwei Liu · 2023 · ICCV 2023 (RangeFormer)
> arXiv:2303.05367 (2303.05367v3, 2023-09-03) · ICCV 2023; 24 pages, 10 figures, 14 tables; Webpage at https://ldkong.com/RangeFormer

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.5 (ref `[27]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[27]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Polar / range-view output parameterisation*. Bearing-indexed 2D output is a workable parameterisation — including its failure modes.

## Your take (your words — authoritative, not ai-draft)
> **Take:** evidence that a bearing-indexed 2D output is a workable parameterisation for our lidar — including the failure modes (seam/discontinuity handling) our circular-W CNN already faces.

## Abstract (from arXiv)
LiDAR segmentation is crucial for autonomous driving perception. Recent trends favor point- or
voxel-based methods as they often yield better performance than the traditional range view
representation. In this work, we unveil several key factors in building powerful range view models.
We observe that the "many-to-one" mapping, semantic incoherence, and shape deformation are possible
impediments against effective learning from range view projections. We present RangeFormer -- a
full-cycle framework comprising novel designs across network architecture, data augmentation, and
post-processing -- that better handles the learning and processing of LiDAR point clouds from the
range view. We further introduce a Scalable Training from Range view (STR) strategy that trains on
arbitrary low-resolution 2D range images, while still maintaining satisfactory 3D segmentation
accuracy. We show that, for the first time, a range view method is able to surpass the point, voxel,
and multi-view fusion counterparts in the competing LiDAR semantic and panoptic segmentation
benchmarks, i.e., SemanticKITTI, nuScenes, and ScribbleKITTI.

## Concepts
- [[occupancy-anticipation]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/2303.05367 (2303.05367v3, published 2023-03-09, updated 2023-09-03)
- DOI: https://doi.org/10.48550/arXiv.2303.05367
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.5.
