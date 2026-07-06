---
type: paper
citekey: fan2020deep
tags: [control, rl]
aliases: []
created: '2026-07-05'
modified: '2026-07-06'
authors:
- David D Fan
- Ali-akbar Agha-mohammadi
- Evangelos A Theodorou
year: 2020
venue: 'Robotics: Science and Systems'
doi: null
arxiv: 2002.01587
url: https://arxiv.org/abs/2002.01587
pdf: attachments/@fan2020deep.pdf
zotero: null
status: to-read
summary: ai-draft
mine: false
bibkeys:
- Fan2020
- fanDeepLearningTubes2020
---

# Deep Learning Tubes for Tube MPC

> [!info] David D. Fan; Ali-akbar Agha-mohammadi; Evangelos A. Theodorou · 2020 · Robotics: Science and Systems (RSS)

> [!note] AI-drafted from the arXiv abstract (not full text) — a base to edit. Flip `summary: ai-draft` → `reviewed` once you've checked it.

## Summary
**TL;DR** — Learns probabilistic *tubes* bounding the trajectory distribution of a learned dynamics model via **deep quantile regression**, then uses them in a Tube MPC that is provably recursively feasible and satisfies constraints with a chosen probability.
**Problem** — Learning-based control needs uncertainty (from limited data or inherent stochasticity) propagated forward through learned nonlinear dynamics to give safety guarantees; that forward propagation is the hard part.
**Method** — A deep quantile-regression framework enforcing probabilistic quantile bounds and quantifying epistemic uncertainty; three approaches for learning tubes that contain the system's possible trajectories, each dropped into a Tube MPC scheme.
**Key results** — Proves recursive feasibility and probabilistic constraint satisfaction; validated in simulation on a nonlinear quadrotor.

## Takeaways
- Learned, **probabilistic (quantile) tubes** as an alternative to hand-derived worst-case bounds — the conceptual lineage your DTMPC extends.
- Quantile regression → α-coverage tubes (compare DTMPC's α-quantile "check loss").
- Guarantees are recursive-feasibility + probabilistic; demonstrated in **sim on a quadrotor**, not on hardware.

## Relevance to your work
Closest prior art to your [[@compton2025dynamic|Dynamic Tube MPC]] — both learn tubes for Tube MPC. DTMPC's departure: an **action-dependent / error-history dynamic tube** learned from **massively parallel simulation** and deployed on hardware (ARCHER). This is the "deep learning tubes" baseline you cite (ref [18]) and contrast against.

## Concepts
- [[dynamic-tube]] · [[tube-mpc]] · [[tracking-error-bound]]

## Source
- arXiv: https://arxiv.org/abs/2002.01587 · PDF: `attachments/@fan2020deep.pdf`
- Cited by [[@compton2025dynamic]]
- bibkeys: `Fan2020`
