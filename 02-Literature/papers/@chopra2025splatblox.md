---
type: paper
citekey: chopra2025splatblox
tags: [navigation, planning]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Chopra, Samarth
- Liang, Jing
- Seneviratne, Gershom
- Lee, Yonghan
- Choi, Jaehoon
- An, Jianyu
- Cheng, Stephen
- Manocha, Dinesh
year: 2025
venue: arXiv
doi: 10.48550/arXiv.2511.18525
arxiv: '2511.18525'
url: http://arxiv.org/abs/2511.18525
zotero: null
summary: ai-draft
pdf: attachments/@chopra2025splatblox.pdf
status: to-read
mine: false
bibkeys:
- chopraSplatbloxTraversabilityAwareGaussian2025
---

# Splatblox: Traversability-Aware Gaussian Splatting for Outdoor Robot Navigation

> [!info] Samarth Chopra; Jing Liang; Gershom Seneviratne; Yonghan Lee; Jaehoon Choi; Jianyu An; Stephen Cheng; Dinesh Manocha · 2025 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A real-time navigation system fuses segmented RGB and LiDAR via Gaussian Splatting into a traversability-aware ESDF that jointly encodes geometry and semantics, letting a robot push through traversable vegetation while avoiding rigid obstacles.
**Problem** — Autonomous navigation in outdoor environments with dense vegetation, irregular obstacles, and complex terrain is hard: geometry alone cannot distinguish traversable tall grass from rigid trees.
**Method** — Fuse segmented RGB images and LiDAR point clouds with Gaussian Splatting to build an online Euclidean Signed Distance Field (ESDF) encoding both geometry and semantics; semantic reasoning separates traversable vegetation from rigid obstacles while LiDAR gives 360-degree geometric coverage for longer planning horizons.
**Key results** — Validated on a quadruped and transferred to a wheeled platform; in vegetation-rich field trials it beats SOTA by over 50% higher success rate, 40% fewer freezing incidents, 5% shorter paths, and up to 13% faster time to goal, supporting missions up to 100 m.

## Takeaways
- Gaussian-splatting representation carries semantics into a signed-distance field, so the planner reasons about "what" as well as "where."
- Semantic traversability lets the robot treat tall grass as passable rather than freezing — a direct fix for the "frozen robot" failure mode.
- Cross-embodiment: same system runs on a quadruped and a wheeled robot.

## Relevance to your work
Core to capability-aware / traversability-aware navigation: encoding semantic traversability (passable vegetation vs. rigid obstacle) in the map is exactly the kind of capability-conditioned map a humanoid planner needs to decide what the G1 can walk through versus around.

## Abstract (from bib)
We present Splatblox, a real-time system for autonomous navigation in outdoor environments with dense vegetation, irregular obstacles, and complex terrain. Our method fuses segmented RGB images and LiDAR point clouds using Gaussian Splatting to construct a traversability-aware Euclidean Signed Distance Field (ESDF) that jointly encodes geometry and semantics. Updated online, this field enables semantic reasoning to distinguish traversable vegetation (e.g., tall grass) from rigid obstacles (e.g., trees), while LiDAR ensures 360-degree geometric coverage for extended planning horizons. We validate Splatblox on a quadruped robot and demonstrate transfer to a wheeled platform. In field trials across vegetation-rich scenarios, it outperforms state-of-the-art methods with over 50\% higher success rate, 40\% fewer freezing incidents, 5\% shorter paths, and up to 13\% faster time to goal, while supporting long-range missions up to 100 meters. Experiment videos and more details can be found on our project page: https://splatblox.github.io

## Concepts
- [[traversability-estimation]]

## Source
- bibkeys: `chopraSplatbloxTraversabilityAwareGaussian2025`
- arXiv: http://arxiv.org/abs/2511.18525
- DOI: https://doi.org/10.48550/arXiv.2511.18525
- URL: http://arxiv.org/abs/2511.18525
