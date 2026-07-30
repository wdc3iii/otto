---
type: paper
citekey: liao2025beyondmimic
tags: []
aliases: []
created: '2026-07-05'
modified: 2026-07-29
authors:
- Liao, Qiayuan
- Truong, Takara E.
- Huang, Xiaoyu
- Tevet, Guy
- Sreenath, Koushil
- Liu, C. Karen
year: 2025
venue: arXiv
doi: 10.48550/arXiv.2508.08241
arxiv: '2508.08241'
url: https://arxiv.org/abs/2508.08241
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@liao2025beyondmimic.pdf
bibkeys:
- liao2025beyondmimic
- liao_beyondmimic_2025
---

# BeyondMimic: From Motion Tracking to Versatile Humanoid Control via Guided Diffusion

> [!info] Liao, Qiayuan; Truong, Takara E.; Huang, Xiaoyu; Tevet, Guy; Sreenath, Koushil; Liu, C. Karen · 2025 · arXiv

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A single motion-tracking formulation masters a wide range of extremely agile humanoid skills, and a latent diffusion model composes them with test-time guidance to solve unseen downstream tasks zero-shot on hardware.
**Problem** — Learning versatile humanoid whole-body control from human demonstrations is limited by two gaps: prior methods either produce unnatural motion or need motion-specific tuning, and they tend to be motion-/goal-specific, unable to compose diverse skills for unseen tasks.
**Method** — A compact motion-tracking formulation learns radically agile behaviors (aerial cartwheels, spin-/flip-kicks, sprinting) with a single setup and shared hyperparameters. A unified latent diffusion model then distills these primitives; classifier guidance provides diffusion-specific test-time optimization toward novel objectives, enabling goal specification, task switching, and dynamic composition.
**Key results** — Achieves state-of-the-art human-like motion quality, and extends zero-shot to tasks unseen in training — motion inpainting, joystick teleoperation, obstacle avoidance — transferring directly to real hardware.

## Takeaways
- One shared tracking setup + hyperparameters spans wildly different agile skills, sidestepping the usual per-motion reward engineering.
- Guided diffusion turns a library of tracked primitives into a composable skill space, with classifier guidance doing test-time steering toward new goals.
- Demonstrates zero-shot sim-to-real transfer for the composed behaviors, not just single tracked clips.
- **Its reward-tuning-free design made it the field's measuring stick** (added 2026-07-29): [[@araujo2025retargeting|GMR]] uses BeyondMimic *specifically because* it needs no reward tuning, making it a neutral instrument for isolating retargeting quality; [[@luo2025sonic|SONIC]] adopts its environment settings and success metric as the basis for scaling up, then reports superseding it (98.7% vs. 81.6% success, MPJPE-L 23.2 vs. 39.1 mm).

## Abstract (from bib)
Learning skills from human motions offers a promising path toward generalizable policies for versatile humanoid whole-body control, yet two key cornerstones are missing: (1) a high-quality motion tracking framework that faithfully transforms large-scale kinematic references into robust and extremely dynamic motions on real hardware, and (2) a distillation approach that can effectively learn these motion primitives and compose them to solve downstream tasks. We address these gaps with BeyondMimic, a real-world framework to learn from human motions for versatile and naturalistic humanoid control via guided diffusion. Our framework provides a motion tracking pipeline capable of challenging skills such as jumping spins, sprinting, and cartwheels with state-of-theart motion quality. Moving beyo

## Concepts
<!-- filled 2026-07-29 (ai-draft) — this section was empty; grounded in the abstract + takeaways above. -->
- [[motion-imitation]] — tracked primitives from human motion, one setup across agile skills.
- [[diffusion-model]] · [[diffusion-policy]] — guided diffusion composes the tracked primitives, with
  classifier guidance steering at test time.
- [[sim-to-real-transfer]] — zero-shot transfer of the *composed* behaviors.

## Relevance to your work
A state-of-the-art point of comparison for learned agile humanoid control: it shows how diffusion-based skill composition scales imitation to versatile, unseen tasks — a contrast to stability-certified, CLF-guided approaches like [[@olkin2026chasing]].

## Source
- Cited by [[@dai2025walk]], [[@olkin2026stability]], [[@terrain2026consistent]]
- bibkeys: `liao2025beyondmimic`, `liao_beyondmimic_2025`
- arXiv: https://arxiv.org/abs/2508.08241
- DOI: https://doi.org/10.48550/arXiv.2508.08241
