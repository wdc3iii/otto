---
type: paper
citekey: cui2024adapting
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Cui, Wenhao
- Li, Shengtao
- Huang, Huaxing
- Qin, Bangyu
- Zhang, Tianchu
- hanjinchao
- Zheng, Liang
- Tang, Ziyang
- Hu, Chenxu
- Yan, Ning
- Chen, Jiahao
- Jiang, Zheyuan
year: 2024
venue: null
doi: null
arxiv: null
url: https://proceedings.mlr.press/v270/cui25a.html
zotero: null
summary: ai-draft
pdf: attachments/@cui2024adapting.pdf
status: to-read
mine: false
bibkeys:
- cui_adapting_2024
---

# Adapting Humanoid Locomotion over Challenging Terrain via Two-Phase Training

> [!info] Cui, Wenhao; Li, Shengtao; Huang, Huaxing; Qin, Bangyu; Zhang, Tianchu; hanjinchao · 2024 · —

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A two-phase RL training framework that produces adaptable, low-oscillation humanoid locomotion over challenging terrain with successful sim-to-real transfer.
**Problem** — Learning-based legged locomotion still struggles with velocity-tracking accuracy at high speeds and on uneven ground, and with joint oscillations that appear on real hardware.
**Method** — A two-phase training paradigm with reinforcement learning, augmented by command curriculum learning to sharpen tracking precision and adaptability. The authors adapt DreamWaQ (an implicit terrain-estimation / privileged-learning locomotion pipeline) to their humanoid and modify it to suppress joint oscillations, then transfer to hardware.
**Key results** — Reports superior performance versus state-of-the-art baselines and a successful sim-to-real deployment (no specific numbers seen in the abstract).

## Takeaways
- Two-phase training plus a command curriculum is presented as the key to robust tracking on uneven terrain.
- Explicitly targets joint oscillation on real humanoids — a practical sim-to-real pain point — via modifications to DreamWaQ.
- Abstract is light on quantitative detail; treat performance claims as unverified until the paper is read.

## Relevance to your work
A representative end-to-end RL locomotion recipe for humanoids on rough terrain, cited by [[@dai2025walk]] as a learning-based point of comparison to foothold-constrained / model-based walking.

## Abstract (from bib)
Humanoid robots are a key focus in robotics, with their capacity to navigate tough terrains being essential for many uses. While strides have been made, creating adaptable locomotion for complex environments is still tough. Recent progress in learning-based systems offers hope for robust legged locomotion, but challenges persist, such as tracking accuracy at high speeds and on uneven ground, and joint oscillations in actual robots. This paper proposes a novel training framework to address these challenges by employing a two-phase training paradigm with reinforcement learning. The proposed framework is further enhanced through the integration of command curriculum learning, refining the precision and adaptability of our approach. Additionally, we adapt DreamWaQ to our humanoid locomotion sy

## Concepts
[[massively-parallel-simulation]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `cui_adapting_2024`
