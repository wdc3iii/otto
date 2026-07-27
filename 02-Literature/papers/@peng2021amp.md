---
type: paper
citekey: peng2021amp
tags: []
aliases: []
created: '2026-07-26'
modified: '2026-07-26'
authors:
- Peng, Xue Bin
- Ma, Ze
- Abbeel, Pieter
- Levine, Sergey
- Kanazawa, Angjoo
year: 2021
venue: SIGGRAPH
doi: 10.48550/arXiv.2104.02180
arxiv: '2104.02180'
url: https://arxiv.org/abs/2104.02180
zotero: null
status: to-read
mine: false
pdf: attachments/@peng2021amp.pdf
---

# AMP: Adversarial Motion Priors for Stylized Physics-Based Character Control

> [!info] Peng, Xue Bin; Ma, Ze; Abbeel, Pieter; Levine, Sergey; Kanazawa, Angjoo · 2021 · SIGGRAPH

> [!todo] metadata-only stub — flesh out from full text when read.

## Concepts
- [[motion-imitation]]

*proposed link — concept note to be created centrally.*

## Abstract (from arXiv)
Synthesizing graceful and life-like behaviors for physically simulated characters has been a fundamental challenge in computer animation. Data-driven methods that leverage motion tracking are a prominent class of techniques for producing high fidelity motions for a wide range of behaviors. However, the effectiveness of these tracking-based methods often hinges on carefully designed objective functions, and when applied to large and diverse motion datasets, these methods require significant additional machinery to select the appropriate motion for the character to track in a given scenario. In this work, we propose to obviate the need to manually design imitation objectives and mechanisms for motion selection by utilizing a fully automated approach based on adversarial imitation learning. High-level task objectives that the character should perform can be specified by relatively simple reward functions, while the low-level style of the character's behaviors can be specified by a dataset of unstructured motion clips, without any explicit clip selection or sequencing. These motion clips are used to train an adversarial motion prior, which specifies style-rewards for training the character through reinforcement learning (RL). The adversarial RL procedure automatically selects which motion to perform, dynamically interpolating and generalizing from the dataset. Our system produces high-quality motions that are comparable to those achieved by state-of-the-art tracking-based techniques, while also being able to easily accommodate large datasets of unstructured motion clips. Composition of disparate skills emerges automatically from the motion prior, without requiring a high-level motion planner or other task-specific annotations of the motion clips. We demonstrate the effectiveness of our framework on a diverse cast of complex simulated characters and a challenging suite of motor control tasks.

## Source
- https://arxiv.org/abs/2104.02180
- DOI: https://doi.org/10.48550/arXiv.2104.02180
