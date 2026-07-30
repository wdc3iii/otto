---
type: paper
citekey: miki2022learning
tags: []
aliases: []
created: '2026-07-05'
modified: 2026-07-29
authors:
- Miki, Takahiro
- Lee, Joonho
- Hwangbo, Jemin
- Wellhausen, Lorenz
- Koltun, Vladlen
- Hutter, Marco
year: 2022
venue: Science Robotics
doi: 10.1126/scirobotics.abk2822
arxiv: 2201.08117
url: https://doi.org/10.1126/scirobotics.abk2822
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@miki2022learning.pdf
bibkeys:
- miki2022learning
- miki_learning_2022
- mikiLearningRobustPerceptive2022
---

# Learning robust perceptive locomotion for quadrupedal robots in the wild

> [!info] Miki, Takahiro; Lee, Joonho; Hwangbo, Jemin; Wellhausen, Lorenz; Koltun, Vladlen; Hutter, Marco · 2022 · Science Robotics
> [!info]- otto authors: [[marco-hutter]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — An attention-based recurrent encoder fuses proprioception and exteroception end-to-end, yielding a quadrupedal locomotion controller robust enough to hike the Alps at human pace.
**Problem** — Exteroception lets a robot plan its gait before contact, but in the wild it is unreliable: snow, vegetation, and water look like obstacles, and depth degrades under poor lighting, dust, fog, occlusion, or reflective/transparent surfaces. Most robust systems therefore fall back on proprioception alone, which caps speed and stability.
**Method** — A learned attention-based recurrent belief encoder integrates proprioceptive and exteroceptive (elevation-map) inputs, trained end-to-end so the policy seamlessly weights each modality by its reliability rather than via hand-tuned heuristics; when terrain perception is untrustworthy the controller gracefully reverts to proprioception. Trained in simulation and deployed on ANYmal.
**Key results** — Demonstrated on the ANYmal quadruped across varied natural and urban terrain over multiple seasons, including an hour-long alpine hike completed within the time recommended for human hikers.

## Takeaways
- The core idea is learned modality fusion via an attention/belief-state encoder — exteroception is trusted only when it agrees with proprioception, giving graceful degradation instead of catastrophic failure on deceptive terrain.
- End-to-end training in simulation transferred to hardware and generalized across seasons and environments, a landmark demonstration of perceptive legged locomotion in the wild.
- Robustness comes from data-driven fusion, not explicit terrain classification or guarantees.

## Relevance to your work
A flagship result for learned perceptive locomotion; useful contrast to guarantee-driven, model-based hierarchies like [[@hierarchies2025motion]] where reduced-order structure and formal certificates replace end-to-end black-box fusion.

## Concepts
<!-- filled 2026-07-29 (ai-draft) — this section was empty; grounded in your own annotation of this
     paper in [[auxiliary-prediction-heads]] §8.3, ref [13]. -->
- [[privileged-information]] — the reference implementation of "reconstruct the privileged signal from a
  recurrent belief": a 2-layer belief GRU (50 units) with an attention gate on exteroception, decoder
  reconstructing **noiseless height samples** + contacts/forces/friction. Objective `L_bc + 0.5·L_re`.
- [[auxiliary-task-learning]] — **the closest existing analogue** of [[auxiliary-prediction-heads]], with
  a published loss weight. Caveat you flagged: the setting is **distillation**, so the aux loss competes
  with a BC loss rather than a policy gradient — the main transfer risk to your PPO setting.
- [[belief-state]] — the gated/reconstructing variant tracks the teacher better under noise (§S9).
- [[rl-for-legged-locomotion]] · [[traversability-estimation]] · [[sim-to-real-transfer]]

## Source
- Cited by [[@compton2024constructive]], [[@csomayshanklin2024robust]], [[@hierarchies2025motion]]
- bibkeys: `miki2022learning`, `miki_learning_2022`
