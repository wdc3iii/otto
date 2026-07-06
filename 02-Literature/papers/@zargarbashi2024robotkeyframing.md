---
type: paper
citekey: zargarbashi2024robotkeyframing
tags: [locomotion, rl, control]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Zargarbashi, Fatemeh
- Cheng, Jin
- Kang, Dongho
- Sumner, Robert
- Coros, Stelian
year: 2024
venue: arXiv
doi: 10.48550/arXiv.2407.11562
arxiv: '2407.11562'
url: http://arxiv.org/abs/2407.11562
zotero: null
summary: ai-draft
pdf: attachments/@zargarbashi2024robotkeyframing.pdf
status: to-read
mine: false
bibkeys:
- zargarbashiRobotKeyframingLearningLocomotion2024
---

# RobotKeyframing: Learning Locomotion with High-Level Objectives via Mixture of Dense and Sparse Rewards

> [!info] Fatemeh Zargarbashi; Jin Cheng; Dongho Kang; Robert Sumner; Stelian Coros · 2024 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A keyframing control framework lets legged robots satisfy a variable number of partial/complete pose targets placed arbitrarily in time, using a multi-critic RL algorithm plus a transformer encoder over timed targets.
**Problem** — Injecting high-level objectives into natural legged locomotion is hard when objectives are a variable number of partial or complete pose targets spaced arbitrarily in time, mixing dense and sparse reward signals.
**Method** — A learning-based control framework using keyframing: a multi-critic RL algorithm to handle the mixture of dense and sparse rewards, and a transformer-based encoder that accommodates a variable number of input targets each tagged with a time-to-arrival.
**Key results** — In simulation and hardware, the framework satisfies target keyframe sequences at the required times; the multi-critic method significantly cuts hyperparameter-tuning effort versus a single critic, and the transformer encoder lets robots anticipate future goals, quantitatively improving target-reaching (no numeric figures read).

## Takeaways
- Keyframing as the interface for high-level objectives — variable-count, arbitrarily-timed partial/full pose targets, each with a time-to-arrival.
- Multi-critic RL to cleanly separate dense vs. sparse reward channels, reducing reward-weight hyperparameter tuning.
- Transformer encoder over timed targets gives anticipation of future goals, improving reach accuracy.

## Relevance to your work
Relevant to RL locomotion with high-level task conditioning — the multi-critic split for dense/sparse rewards and the timed-target transformer are transferable ideas for goal- or path-conditioned humanoid locomotion on the G1, where you want natural gaits that hit pose/timing objectives.

## Abstract (from bib)
This paper presents a novel learning-based control framework that uses keyframing to incorporate high-level objectives in natural locomotion for legged robots. These high-level objectives are specified as a variable number of partial or complete pose targets that are spaced arbitrarily in time. Our proposed framework utilizes a multi-critic reinforcement learning algorithm to effectively handle the mixture of dense and sparse rewards. Additionally, it employs a transformer-based encoder to accommodate a variable number of input targets, each associated with specific time-to-arrivals. Throughout simulation and hardware experiments, we demonstrate that our framework can effectively satisfy the target keyframe sequence at the required times. In the experiments, the multi-critic method significantly reduces the effort of hyperparameter tuning compared to the standard single-critic alternative. Moreover, the proposed transformer-based architecture enables robots to anticipate future goals, which results in quantitative improvements in their ability to reach their targets.

## Concepts
- [[rl-for-legged-locomotion]]

## Source
- bibkeys: `zargarbashiRobotKeyframingLearningLocomotion2024`
- arXiv: http://arxiv.org/abs/2407.11562
- DOI: https://doi.org/10.48550/arXiv.2407.11562
- URL: http://arxiv.org/abs/2407.11562
