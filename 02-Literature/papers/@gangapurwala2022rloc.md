---
type: paper
citekey: gangapurwala2022rloc
tags: [locomotion, rl, control]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Gangapurwala, Siddhant
- Geisert, Mathieu
- Orsolino, Romeo
- Fallon, Maurice
- Havoutis, Ioannis
year: 2022
venue: IEEE Transactions on Robotics
doi: 10.1109/TRO.2022.3172469
arxiv: '2012.03094'
url: http://arxiv.org/abs/2012.03094
zotero: null
summary: ai-draft
pdf: attachments/@gangapurwala2022rloc.pdf
status: to-read
mine: false
bibkeys:
- gangapurwalaRLOCTerrainAwareLegged2022
---

# RLOC: Terrain-Aware Legged Locomotion Using Reinforcement Learning and Optimal Control

> [!info] Siddhant Gangapurwala; Mathieu Geisert; Romeo Orsolino; Maurice Fallon; Ioannis Havoutis · 2022 · IEEE Transactions on Robotics

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A hybrid model-based + data-driven quadrupedal framework where an RL policy maps sensory + velocity commands into footstep plans that a model-based controller then tracks, achieving dynamic locomotion over uneven terrain.
**Problem** — Achieving dynamic, robust quadrupedal locomotion over uneven terrain by combining the strengths of learned planning and model-based control.
**Method** — An RL policy (trained in simulation over procedurally generated terrains) maps proprioceptive + exteroceptive feedback and desired base-velocity commands into footstep plans; online, a model-based motion controller tracks those plans. Two ancillary RL policies handle corrective whole-body motion tracking and recovery control to account for parameter changes and external perturbations.
**Key results** — Evaluated over a wide variety of complex terrains with behavior prioritizing stability over aggressive locomotion; trained/evaluated on ANYmal B and shown to transfer to the larger, heavier ANYmal C without retraining (no numeric figures read).

## Takeaways
- Clean division of labor: RL produces footstep plans, optimal/model-based control executes them — learning where to step, model-based control for how.
- Ancillary RL policies for whole-body tracking correction and recovery add robustness to parameter shifts and perturbations.
- Zero-shot cross-platform transfer (ANYmal B → C) without retraining.

## Relevance to your work
Squarely on your central line — combining RL policies with classical planning/control for legged locomotion. RLOC's RL-plans-footsteps / model-based-tracks decomposition is a direct template for the hierarchical RL+control architectures you build on the G1.

## Abstract (from bib)
We present a unified model-based and data-driven approach for quadrupedal planning and control to achieve dynamic locomotion over uneven terrain. We utilize on-board proprioceptive and exteroceptive feedback to map sensory information and desired base velocity commands into footstep plans using a reinforcement learning (RL) policy. This RL policy is trained in simulation over a wide range of procedurally generated terrains. When ran online, the system tracks the generated footstep plans using a model-based motion controller. We evaluate the robustness of our method over a wide variety of complex terrains. It exhibits behaviors which prioritize stability over aggressive locomotion. Additionally, we introduce two ancillary RL policies for corrective whole-body motion tracking and recovery control. These policies account for changes in physical parameters and external perturbations. We train and evaluate our framework on a complex quadrupedal system, ANYmal version B, and demonstrate transferability to a larger and heavier robot, ANYmal C, without requiring retraining.

## Concepts
- [[rl-for-legged-locomotion]]
- [[hierarchical-control]]
- [[sim-to-real-transfer]]

## Source
- bibkeys: `gangapurwalaRLOCTerrainAwareLegged2022`
- arXiv: http://arxiv.org/abs/2012.03094
- DOI: https://doi.org/10.1109/TRO.2022.3172469
- URL: http://arxiv.org/abs/2012.03094
