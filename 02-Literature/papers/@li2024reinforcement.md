---
type: paper
citekey: li2024reinforcement
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Li, Zhongyu
- Peng, Xue Bin
- Abbeel, Pieter
- Levine, Sergey
- Berseth, Glen
- Sreenath, Koushil
year: 2024
venue: arXiv preprint arXiv:2401.16889
doi: null
arxiv: '2401.16889'
url: https://arxiv.org/abs/2401.16889
summary: ai-draft
pdf: attachments/@li2024reinforcement.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- Li2024
- li2024reinforcementlearningversatiledynamic
---

# Reinforcement learning for versatile, dynamic, and robust bipedal locomotion control

> [!info] Li, Zhongyu; Peng, Xue Bin; Abbeel, Pieter; Levine, Sergey; Berseth, Glen; Sreenath, Koushil · 2024 · arXiv preprint arXiv:2401.16889
> [!info]- otto authors: [[sergey-levine]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A single end-to-end deep-RL controller that produces a broad range of dynamic bipedal skills — walking, running, jumping, standing — on the Cassie robot, using a dual-history policy architecture.
**Problem** — Most RL locomotion controllers target one skill; the gap is a general control solution that spans periodic (walking/running) and aperiodic (jumping/standing) behaviors while remaining robust and deployable on real hardware.
**Method** — An RL controller with a novel dual-history architecture that ingests both long-term and short-term I/O history of the robot, trained end-to-end. The I/O history lets the policy adapt to time-invariant dynamics shifts and time-variant events (e.g., contacts); task randomization is identified as a second key robustness source.
**Key results** — Outperforms baselines across diverse skills in sim and real; deployed on torque-controlled Cassie with robust standing, versatile walking, fast running (a 400 m dash), and standing long/high jumps.

## Takeaways
- The dual-history (long- + short-term I/O) input is the core mechanism for implicit system identification and contact adaptation without explicit state estimation.
- Task randomization — not just dynamics randomization — is highlighted as a distinct driver of generalization and disturbance rejection.
- Demonstrates that one policy can cover periodic and aperiodic skills, pushing the agility envelope for torque-controlled bipeds.

## Relevance to your work
A strong data point on how far model-free RL alone pushes robust, agile bipedal locomotion — useful contrast for control-theoretic / reduced-order approaches like [[@csomayshanklin2024robust]] that seek formal tracking guarantees rather than learned robustness.

## Concepts

## Source
- Cited by [[@compton2025dynamic]], [[@csomayshanklin2024robust]]
- bibkeys: `Li2024`, `li2024reinforcementlearningversatiledynamic`
- arXiv: https://arxiv.org/abs/2401.16889
