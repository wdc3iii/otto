---
type: paper
citekey: gu2024advancing
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Gu, Xinyang
- Wang, Yen-Jen
- Zhu, Xiang
- Shi, Chengming
- Guo, Yanjiang
- Liu, Yichen
- Chen, Jianyu
year: 2024
venue: 'Robotics: Science and Systems XX'
doi: 10.15607/RSS.2024.XX.058
arxiv: 2408.14472
url: https://arxiv.org/abs/2408.14472
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@gu2024advancing.pdf
bibkeys:
- gu_advancing_2024
---

# Advancing Humanoid Locomotion: Mastering Challenging Terrains with Denoising World Model Learning

> [!info] Gu, Xinyang; Wang, Yen-Jen; Zhu, Xiang; Shi, Chengming; Guo, Yanjiang; Liu, Yichen · 2024 · Robotics: Science and Systems XX

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Denoising World Model Learning (DWL), an end-to-end RL framework that produces a single humanoid locomotion policy transferring zero-shot to a wide range of real-world challenging terrains.
**Problem** — Learned humanoid controllers struggle to generalize and transfer robustly from simulation to genuinely hard real-world terrain (snow, inclines, stairs, highly uneven ground).
**Method** — An end-to-end reinforcement-learning framework that learns a denoising world model, coupling world-model learning with policy learning to improve robustness and sim-to-real transfer.
**Key results** — Reported as the first humanoid to master real-world terrains including snowy/inclined ground, stairs, and extremely uneven terrain in the wild, all with a single learned network transferred zero-shot from simulation (per the authors' abstract).

## Takeaways
- Denoising a learned world model is used as the mechanism for robustness and generalization, not just a reward-shaping trick.
- One policy, zero-shot sim-to-real across diverse terrains, is the headline claim — strong generalization argument for end-to-end RL on humanoids.
- Claims are from the abstract; the specific denoising formulation and quantitative comparisons should be checked in the paper before citing precisely.

## Relevance to your work
A state-of-the-art end-to-end RL humanoid locomotion result that a learning-to-walk approach like [[@dai2025walk]] would benchmark against or contrast with structurally (learned world model vs. model-based/hierarchical structure).

## Concepts
[[massively-parallel-simulation]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `gu_advancing_2024`
- DOI: https://doi.org/10.15607/RSS.2024.XX.058
