---
type: paper
citekey: zhang2026ame
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-06'
authors:
- Zhang, Chong
- Klemm, Victor
- Yang, Fan
- Hutter, Marco
year: 2026
venue: arXiv preprint arXiv:2601.08485
doi: null
arxiv: '2601.08485'
url: https://arxiv.org/abs/2601.08485
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@zhang2026ame.pdf
bibkeys:
- zhang2026ame
- zhangAME2AgileGeneralized2026
---

# AME-2: Agile and Generalized Legged Locomotion via Attention-Based Neural Map Encoding

> [!info] Zhang, Chong; Klemm, Victor; Yang, Fan; Hutter, Marco · 2026 · arXiv preprint arXiv:2601.08485
> [!info]- otto authors: [[fan-yang]] · [[marco-hutter]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — AME-2 is a unified RL framework for agile *and* generalized legged locomotion built around an attention-based map encoder plus a learning-based, uncertainty-aware mapping pipeline, validated on a quadruped and a biped.
**Problem** — Prior agile parkour policies rely on end-to-end sensorimotor models with poor generalization/interpretability, while generalized-locomotion methods lack agility and fail under visual occlusions. AME-2 aims to get both at once, robustly under occlusions and sparse footholds.
**Method** — A novel attention-based map encoder extracts local and global terrain features and attends to salient regions, yielding an interpretable, generalized embedding for the RL control policy. A separate learning-based mapping pipeline converts depth observations into local elevation maps with per-cell uncertainty and fuses them with odometry; it integrates with parallel simulation so controllers train with online mapping, aiding sim-to-real transfer.
**Key results** — Controllers demonstrate strong agility and generalization to unseen terrains in both simulation and real-world experiments on a quadruped (ANYmal-D) and a biped (LimX TRON1).

## Takeaways
- Attention over an elevation-map encoding gives an interpretable, generalizable terrain embedding — a middle path between opaque end-to-end policies and hand-crafted features.
- Explicitly modeling terrain uncertainty and training with online mapping in parallel simulation is the mechanism for robustness to occlusions and sim-to-real transfer.
- Single framework validated across both quadruped and biped morphologies.

## Relevance to your work
Represents the perception-in-the-loop, massively-parallel-trained RL end of legged locomotion, contrasting with model-based reduced-order approaches; a current benchmark for terrain-aware agility relevant to [[@dai2025walk]].

## Concepts
[[massively-parallel-simulation]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `zhang2026ame`
- arXiv: https://arxiv.org/abs/2601.08485
