---
type: paper
citekey: bang2024rl
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Bang, Seung Hyeon
- Jové, Carlos Arribalzaga
- Sentis, Luis
year: 2024
venue: arXiv:2407.17683 [cs]
doi: 10.48550/arXiv.2407.17683
arxiv: '2407.17683'
url: https://arxiv.org/abs/2407.17683
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@bang2024rl.pdf
bibkeys:
- bang_rl-augmented_2024
---

# RL-augmented MPC Framework for Agile and Robust Bipedal Footstep Locomotion Planning and Control

> [!info] Bang, Seung Hyeon; Jové, Carlos Arribalzaga; Sentis, Luis · 2024 · arXiv:2407.17683 [cs]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — An RL-augmented MPC footstep planner where a learned policy refines an ALIP-based MPC's foot-placement decisions, bridging the reduced-order model and the full-order humanoid.

**Problem** — MPC foot-placement controllers work well but are limited by simplified template models and their assumptions, capping agility and robustness on the real full-order robot.

**Method** — Combine an ALIP (Angular-momentum Linear Inverted Pendulum) MPC for sub-optimal footstep planning with a learned policy that refines the footstep adjustments; the RL correction lets the resulting footstep policy account for whole-body dynamics the template model omits, synergizing MPC's predictive structure with RL's adaptability.

**Key results** — On the full-body humanoid DRACO 3, the framework improves dynamic locomotion — better tracking across a wide speed range, reliable turning, and traversal of challenging terrain — while preserving gait robustness/stability versus a baseline ALIP-MPC.

## Abstract (from bib)
This paper proposes an online bipedal footstep planning strategy that combines model predictive control (MPC) and reinforcement learning (RL) to achieve agile and robust bipedal maneuvers. While MPC-based foot placement controllers have demonstrated their effectiveness in achieving dynamic locomotion, their performance is often limited by the use of simplified models and assumptions. To address this challenge, we develop a novel foot placement controller that leverages a learned policy to bridge the gap between the use of a simplified model and the more complex full-order robot system. Specifically, our approach employs a unique combination of an ALIP-based MPC foot placement controller for sub-optimal footstep planning and the learned policy for refining footstep adjustments, enabling the

## Takeaways
- The learned policy is a *residual/refinement* on top of model-based footstep planning, not a replacement — MPC keeps the predictive backbone, RL closes the template-vs-full-order gap.
- ALIP is the reduced-order template; the whole design is a hybrid model-based/learned footstep controller.
- Validated on a full-body humanoid (DRACO 3) with gains in speed-tracking, turning, and terrain robustness over pure ALIP-MPC.

## Relevance to your work
A direct instance of the learning-augmented-MPC footstep pattern — using RL to correct reduced-order-model error while retaining model-based guarantees — closely aligned with the hybrid approach in [[@dai2025walk]].

## Concepts
[[reduced-order-model]] · [[hierarchical-control]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `bang_rl-augmented_2024`
- arXiv: https://arxiv.org/abs/2407.17683
