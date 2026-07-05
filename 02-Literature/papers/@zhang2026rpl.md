---
type: paper
citekey: zhang2026rpl
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Zhang, Yuanhang
- Seo, Younggyo
- Chen, Juyue
- Yuan, Yifu
- Sreenath, Koushil
- Abbeel, Pieter
- Sferrazza, Carmelo
- Liu, Karen
- Duan, Rocky
- Shi, Guanya
year: 2026
venue: arXiv preprint arXiv:2602.03002
doi: null
arxiv: '2602.03002'
url: https://arxiv.org/abs/2602.03002
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@zhang2026rpl.pdf
bibkeys:
- zhang2026rpl
---

# RPL: Learning Robust Humanoid Perceptive Locomotion on Challenging Terrains

> [!info] Zhang, Yuanhang; Seo, Younggyo; Chen, Juyue; Yuan, Yifu; Sreenath, Koushil; Abbeel, Pieter · 2026 · arXiv preprint arXiv:2602.03002

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — RPL learns a single transformer-based vision policy for robust, omnidirectional humanoid locomotion over challenging terrain by distilling terrain-specialist experts into a depth-camera-driven controller.

**Problem** — Robust multi-directional humanoid locomotion on complex terrain (slopes, stairs, stepping stones with gaps) from onboard perception, where naïve depth-based policies are brittle to sensor noise and viewpoint.

**Method** — Two-stage training: first train terrain-specific expert policies with privileged observations, then distill them into a single transformer policy that consumes depth-camera input. Robustness comes from scaling depth features by the velocity command and random side-masking of the depth input; an efficient multi-depth rendering system gives a claimed ~5x speedup over existing simulators' depth pipelines while modeling realistic sensor characteristics.

**Key results** — Real-world deployment navigates steep slopes, staircases of varying dimensions, and stepping stones with large gaps, including under added payload. (Specific numeric benchmarks not seen in the abstract.)

## Takeaways
- Expert-then-distill (privileged experts → depth-input transformer student) is the recurring recipe for perceptive legged locomotion; RPL applies it to humanoids with an emphasis on robustness tricks.
- Velocity-conditioned depth-feature scaling and random side-masking are the concrete robustness levers worth remembering.
- Fast, realistic depth rendering in sim is treated as a first-class enabler, not an afterthought.

## Relevance to your work
Directly relevant as a state-of-the-art perceptive humanoid locomotion baseline; its terrain-consistency and depth-perception concerns connect to [[@terrain2026consistent]].

## Concepts
[[massively-parallel-simulation]] [[hierarchical-control]]

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `zhang2026rpl`
- arXiv: https://arxiv.org/abs/2602.03002
