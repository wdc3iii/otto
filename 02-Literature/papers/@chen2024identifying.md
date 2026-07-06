---
type: paper
citekey: chen2024identifying
tags: [navigation, locomotion, method]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Chen, Jiaqi
- Frey, Jonas
- Zhou, Ruyi
- Miki, Takahiro
- Martius, Georg
- Hutter, Marco
year: 2024
venue: arXiv
doi: 10.48550/arXiv.2408.16567
arxiv: '2408.16567'
url: http://arxiv.org/abs/2408.16567
zotero: null
summary: ai-draft
pdf: attachments/@chen2024identifying.pdf
status: to-read
mine: false
bibkeys:
- chenIdentifyingTerrainPhysical2024
---

# Identifying Terrain Physical Parameters from Vision — Towards Physical-Parameter-Aware Locomotion and Navigation

> [!info] Jiaqi Chen; Jonas Frey; Ruyi Zhou; Takahiro Miki; Georg Martius; Marco Hutter · 2024 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A cross-modal self-supervised framework predicts terrain friction and stiffness from vision, anticipating non-geometric hazards (slippery, deformable ground) before contact.
**Problem** — Estimating environmental physical parameters (friction, stiffness) from vision is an open challenge, yet it is essential for handling non-geometric hazards that geometry-only perception misses.
**Method** — Train a physical decoder in simulation to predict friction and stiffness from multi-modal input; use it to self-supervisedly label real-world images with physical parameters, which then train a visual network at deployment that densely predicts friction/stiffness from images — bridging sim-trained policies and real terrain identification.
**Key results** — Validated in simulation and the real world on the ANYmal quadruped, outperforming an existing baseline; the visual network predicts physical properties in indoor and outdoor experiments and adapts quickly to new environments. (no numeric figures read)

## Takeaways
- Separates a sim-trained "physical decoder" (multi-modal → friction/stiffness) from a deployment-time visual network trained on its self-supervised labels.
- Targets non-geometric traversability (friction, deformability) that elevation/geometry maps cannot capture.
- Dense per-pixel physical-parameter prediction is the intended input to future physical-parameter-aware locomotion and navigation.

## Relevance to your work
Squarely relevant to capability-aware navigation: it produces the friction/stiffness fields a capability-aware planner would need to decide where the G1 can safely step or walk fast — the perception half of the terrain-aware locomotion loop.

## Abstract (from bib)
Identifying the physical properties of the surrounding environment is essential for robotic locomotion and navigation to deal with non-geometric hazards, such as slippery and deformable terrains. It would be of great benefit for robots to anticipate these extreme physical properties before contact; however, estimating environmental physical parameters from vision is still an open challenge. Animals can achieve this by using their prior experience and knowledge of what they have seen and how it felt. In this work, we propose a cross-modal self-supervised learning framework for vision-based environmental physical parameter estimation, which paves the way for future physical-property-aware locomotion and navigation. We bridge the gap between existing policies trained in simulation and identification of physical terrain parameters from vision. We propose to train a physical decoder in simulation to predict friction and stiffness from multi-modal input. The trained network allows the labeling of real-world images with physical parameters in a self-supervised manner to further train a visual network during deployment, which can densely predict the friction and stiffness from image data. We validate our physical decoder in simulation and the real world using a quadruped ANYmal robot, outperforming an existing baseline method. We show that our visual network can predict the physical properties in indoor and outdoor experiments while allowing fast adaptation to new environments.

## Concepts
- [[traversability-estimation]]
- [[sim-to-real-transfer]]

## Source
- bibkeys: `chenIdentifyingTerrainPhysical2024`
- arXiv: http://arxiv.org/abs/2408.16567
- DOI: https://doi.org/10.48550/arXiv.2408.16567
- URL: http://arxiv.org/abs/2408.16567
