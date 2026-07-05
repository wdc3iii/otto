---
type: paper
citekey: benndgallant
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Ben, Qingwei
- Xu, Botian
- Li, Kailin
- Jia, Feiyu
- Zhang, Wentao
- Wang, Jingping
- Wang, Jingbo
- Lin, Dahua
- Pang, Jiangmiao
year: null
venue: null
doi: 10.48550/arXiv.2511.14625
arxiv: '2511.14625'
url: http://arxiv.org/abs/2511.14625
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@benndgallant.pdf
bibkeys:
- benGallantVoxelGridbased2025
---

# Gallant: Voxel Grid-based Humanoid Locomotion and Local-navigation across 3D Constrained Terrains

> [!info] Ben, Qingwei; Xu, Botian; Li, Kailin; Jia, Feiyu; Zhang, Wentao; Wang, Jingping · n.d. · —

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Gallant is a voxel-grid-based, end-to-end humanoid locomotion and local-navigation framework that uses voxelized LiDAR as a full-3D perceptual representation, going beyond ground-level obstacles to overhead, lateral, multi-level, and narrow-passage constraints.
**Problem** — Depth-image and elevation-map perception give only partial, locally-flattened views and miss true 3D structure (overhead clearances, multi-level terrain), limiting humanoid locomotion in 3D-constrained environments.
**Method** — Gallant voxelizes LiDAR into a lightweight structured representation and feeds it through a z-grouped 2D CNN to the control policy, enabling fully end-to-end optimization. A high-fidelity LiDAR simulation dynamically generates realistic observations to support scalable LiDAR-based training and sim-to-real consistency.
**Key results** — Broader perceptual coverage lets a single policy handle lateral clutter, overhead constraints, multi-level structures, and narrow passages; reports near-100% success on challenging cases like stair climbing and stepping onto elevated platforms.

## Takeaways
- A full-3D voxel representation (vs. 2.5D elevation maps) is what unlocks overhead/multi-level constraints for humanoids.
- The z-grouped 2D CNN keeps voxel perception lightweight enough for end-to-end policy training.
- High-fidelity LiDAR simulation is the enabler for scalable training and sim-to-real transfer of perception-driven locomotion.

## Relevance to your work
Directly relevant to perception-conditioned humanoid locomotion over complex 3D terrain — a LiDAR/voxel perception approach complementary to the terrain-consistent navigation of [[@terrain2026consistent]].

## Abstract (from bib)
Robust humanoid locomotion requires accurate and globally consistent perception of the surrounding 3D environment. However, existing perception modules, mainly based on depth images or elevation maps, offer only partial and locally flattened views of the environment, failing to capture the full 3D structure. This paper presents Gallant, a voxel-grid-based framework for humanoid locomotion and local navigation in 3D constrained terrains. It leverages voxelized LiDAR data as a lightweight and structured perceptual representation, and employs a z-grouped 2D CNN to map this representation to the control policy, enabling fully end-to-end optimization. A high-fidelity LiDAR simulation that dynamically generates realistic observations is developed to support scalable, LiDAR-based training and ens

## Concepts


## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `benGallantVoxelGridbased2025`
- arXiv: https://arxiv.org/abs/2511.14625
- DOI: https://doi.org/10.48550/arXiv.2511.14625
- URL: http://arxiv.org/abs/2511.14625
