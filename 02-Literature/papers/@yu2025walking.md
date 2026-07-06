---
type: paper
citekey: yu2025walking
tags: [locomotion, rl]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Yu, Ruiqi
- Wang, Qianshi
- Wang, Yizhen
- Wang, Zhicheng
- Wu, Jun
- Zhu, Qiuguo
year: 2025
venue: arXiv
doi: 10.48550/arXiv.2409.15692
arxiv: '2409.15692'
url: http://arxiv.org/abs/2409.15692
zotero: null
summary: ai-draft
pdf: attachments/@yu2025walking.pdf
status: to-read
mine: false
bibkeys:
- yuWalkingTerrainReconstruction2025
---

# Walking with Terrain Reconstruction: Learning to Traverse Risky Sparse Footholds

> [!info] Ruiqi Yu; Qianshi Wang; Yizhen Wang; Zhicheng Wang; Jun Wu; Qiuguo Zhu · 2025 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — End-to-end RL using only proprioception and depth images, with a learned local terrain-reconstruction bottleneck, lets a low-cost quadruped traverse risky terrains with sparse, random footholds.
**Problem** — Traversing sparse-foothold risky terrain needs precise foot placement in safe areas. Heightmaps from mocap/mapping pipelines add noise and complexity; raw egocentric depth has limited FOV and sparse info that is hard to fold into implicit features for precise action.
**Method** — End-to-end RL from proprioception + depth images that introduces *local terrain reconstruction* — reconstructing a heightmap as an intermediary between visual feature extraction and motion generation, so the policy can represent and memorize critical terrain structure.
**Key results** — Deployed on a low-cost quadruped, achieving agile, adaptive locomotion across various challenging terrains with reported strong real-world performance (no numeric figures read).

## Takeaways
- Local terrain reconstruction as an explicit intermediate representation (heightmap) learned from depth, bridging sparse egocentric vision and precise foothold selection.
- Argues the reconstructed heightmap gives clearer features than raw depth for memorizing terrain — a supervised/auxiliary bottleneck inside an end-to-end RL policy.
- Proprioception + depth only (no mocap, no external mapping pipeline), on low-cost hardware.

## Relevance to your work
Squarely on perceptive/terrain-aware locomotion and precise foothold planning — the local-reconstruction bottleneck is a concrete design pattern for turning noisy exteroception into an action-relevant terrain representation, relevant to capability-aware footstep placement on the G1.

## Abstract (from bib)
Traversing risky terrains with sparse footholds presents significant challenges for legged robots, requiring precise foot placement in safe areas. To acquire comprehensive exteroceptive information, prior studies have employed motion capture systems or mapping techniques to generate heightmap for locomotion policy. However, these approaches require specialized pipelines and often introduce additional noise. While depth images from egocentric vision systems are cost-effective, their limited field of view and sparse information hinder the integration of terrain structure details into implicit features, which are essential for generating precise actions. In this paper, we demonstrate that end-to-end reinforcement learning relying solely on proprioception and depth images is capable of traversing risky terrains with high sparsity and randomness. Our method introduces local terrain reconstruction, leveraging the benefits of clear features and sufficient information from the heightmap, which serves as an intermediary for visual feature extraction and motion generation. This allows the policy to effectively represent and memorize critical terrain information. We deploy the proposed framework on a low-cost quadrupedal robot, achieving agile and adaptive locomotion across various challenging terrains and showcasing outstanding performance in real-world scenarios. Video at: youtu.be/Rj9v5EZsn-M.

## Concepts
- [[rl-for-legged-locomotion]]
- [[traversability-estimation]]

## Source
- bibkeys: `yuWalkingTerrainReconstruction2025`
- arXiv: http://arxiv.org/abs/2409.15692
- DOI: https://doi.org/10.48550/arXiv.2409.15692
- URL: http://arxiv.org/abs/2409.15692
