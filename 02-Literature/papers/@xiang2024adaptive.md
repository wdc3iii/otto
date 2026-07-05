---
type: paper
citekey: xiang2024adaptive
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Xiang, Zhaoyang
- Paredes, Victor
- Hereid, Ayonga
year: 2024
venue: arXiv:2403.17136 [cs, eess]
doi: 10.48550/arXiv.2403.17136
arxiv: '2403.17136'
url: https://arxiv.org/abs/2403.17136
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@xiang2024adaptive.pdf
bibkeys:
- xiang_adaptive_2024
---

# Adaptive Step Duration for Precise Foot Placement: Achieving Robust Bipedal Locomotion on Terrains with Restricted Footholds

> [!info] Xiang, Zhaoyang; Paredes, Victor; Hereid, Ayonga · 2024 · arXiv:2403.17136 [cs, eess]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A multi-step-preview foot-placement planner that adapts step duration via a DCM-based discrete-time MPC, enabling robust bipedal walking on foothold-restricted terrains like random stepping stones.
**Problem** — Traditional one-step-preview planners cannot keep bipeds stable when stepping areas are severely restricted (e.g., stepping stones); they lack the lookahead to guarantee viability over future steps.
**Method** — Formulates a discrete-time MPC on the step-to-step evolution of the Divergent Component of Motion (DCM). The optimizer adaptively adjusts step duration (and swing-foot trajectory) for optimal foot placement under foothold constraints, ensuring viability across multiple future steps.
**Key results** — Simulation across complex stepping-stone configurations with external perturbations shows improved robustness and navigation on foothold-restricted terrain versus one-step preview, remaining viable under disturbances.

## Takeaways
- Adapting step *duration* (a timing degree of freedom) — not just step position — is the key lever for foothold-constrained viability.
- Multi-step DCM MPC beats one-step preview precisely when footholds are tight.
- Step-to-step discrete DCM dynamics keep the MPC low-dimensional and tractable.

## Abstract (from bib)
This paper introduces a novel multi-step preview foot placement planning algorithm designed to enhance the robustness of bipedal robotic walking across challenging terrains with restricted footholds. Traditional one-step preview planning struggles to maintain stability when stepping areas are severely limited, such as with random stepping stones. In this work, we developed a discrete-time Model Predictive Control (MPC) based on the step-to-step discrete evolution of the Divergent Component of Motion (DCM) of bipedal locomotion. This approach adaptively changes the step duration for optimal foot placement under constraints, thereby ensuring the robot's operational viability over multiple future steps and significantly improving its ability to navigate through environments with tight constra

## Relevance to your work
A model-based (DCM-MPC) treatment of the same foothold-restricted locomotion problem [[@dai2025walk]] tackles; adaptive step timing over a reduced-order walking model is a classical-planning counterpart to learned foothold policies.

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `xiang_adaptive_2024`
- arXiv: https://arxiv.org/abs/2403.17136
