---
type: paper
citekey: radosavovic2024humanoid
tags: [locomotion, rl]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Radosavovic, Ilija
- Kamat, Sarthak
- Darrell, Trevor
- Malik, Jitendra
year: 2024
venue: arXiv
doi: 10.48550/arXiv.2410.03654
arxiv: '2410.03654'
url: http://arxiv.org/abs/2410.03654
zotero: null
summary: ai-draft
pdf: attachments/@radosavovic2024humanoid.pdf
status: to-read
mine: false
bibkeys:
- radosavovicLearningHumanoidLocomotion2024
---

# Learning Humanoid Locomotion over Challenging Terrain

> [!info] Ilija Radosavovic; Sarthak Kamat; Trevor Darrell; Jitendra Malik · 2024 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A transformer policy for blind humanoid locomotion, pre-trained on flat-ground sequences and RL-fine-tuned on uneven terrain, that traverses diverse challenging surfaces on a real robot.
**Problem** — Building controllers that generalize across diverse terrains is hard: classical controllers don't generalize broadly, and learning methods have mostly targeted gentle terrain.
**Method** — A transformer predicts the next action from a history of proprioceptive observations and actions. It is first pre-trained on a dataset of flat-ground trajectories via sequence modeling, then fine-tuned on uneven terrain with reinforcement learning. The approach is blind (proprioception only).
**Key results** — Robust real-world performance across rough, deformable, and sloped surfaces, with in-context adaptation and emergent terrain representations; the robot traversed over 4 miles of Berkeley hiking trails and climbed some of the steepest San Francisco streets (no other numeric figures read).

## Takeaways
- Two-stage recipe: sequence-model pre-training on flat ground, then RL fine-tuning on uneven terrain.
- Transformer over proprioceptive history enables in-context adaptation and emergent terrain representations — memory as implicit system ID.
- Blind (proprioception-only) locomotion is enough for a wide terrain range at human scale.

## Relevance to your work
Directly on your line — RL-based humanoid locomotion policies over challenging terrain, blind/proprioceptive. The transformer-with-history recipe and emergent terrain representations are a strong reference point for G1 locomotion policy design and sim-to-real.

## Abstract (from bib)
Humanoid robots can, in principle, use their legs to go almost anywhere. Developing controllers capable of traversing diverse terrains, however, remains a considerable challenge. Classical controllers are hard to generalize broadly while the learning-based methods have primarily focused on gentle terrains. Here, we present a learning-based approach for blind humanoid locomotion capable of traversing challenging natural and man-made terrain. Our method uses a transformer model to predict the next action based on the history of proprioceptive observations and actions. The model is first pre-trained on a dataset of flat-ground trajectories with sequence modeling, and then fine-tuned on uneven terrain using reinforcement learning. We evaluate our model on a real humanoid robot across a variety of terrains, including rough, deformable, and sloped surfaces. The model demonstrates robust performance, in-context adaptation, and emergent terrain representations. In real-world case studies, our humanoid robot successfully traversed over 4 miles of hiking trails in Berkeley and climbed some of the steepest streets in San Francisco.

## Concepts
- [[rl-for-legged-locomotion]]
- [[sim-to-real-transfer]]

## Source
- bibkeys: `radosavovicLearningHumanoidLocomotion2024`
- arXiv: http://arxiv.org/abs/2410.03654
- DOI: https://doi.org/10.48550/arXiv.2410.03654
- URL: http://arxiv.org/abs/2410.03654
