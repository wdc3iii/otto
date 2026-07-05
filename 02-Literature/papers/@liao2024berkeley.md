---
type: paper
citekey: liao2024berkeley
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Liao, Qiayuan
- Zhang, Bike
- Huang, Xuanyu
- Huang, Xiaoyu
- Li, Zhongyu
- Sreenath, Koushil
year: 2024
venue: arXiv preprint arXiv:2407.21781
doi: 10.1109/ICRA55743.2025.11127524
arxiv: '2407.21781'
url: https://arxiv.org/abs/2407.21781
summary: ai-draft
pdf: attachments/@liao2024berkeley.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- Liao2024
---

# Berkeley Humanoid: A Research Platform for Learning-based Control

> [!info] Liao, Qiayuan; Zhang, Bike; Huang, Xuanyu; Huang, Xiaoyu; Li, Zhongyu; Sreenath, Koushil · 2024 · arXiv preprint arXiv:2407.21781

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Introduces Berkeley Humanoid, a low-cost, in-house mid-scale humanoid platform purpose-built for learning-based control, with a narrow sim-to-real gap that enables agile RL locomotion outdoors.
**Problem** — Humanoid research is bottlenecked by expensive, hard-to-simulate, fall-fragile hardware; the gap is a reliable, affordable platform designed around the needs of learning algorithms.
**Method** — A lightweight custom robot engineered for accurate, low-complexity simulation, anthropomorphic motion, and high reliability against falls. A simple RL controller with only light domain randomization exploits the narrow sim-to-real gap for robust locomotion across terrains.
**Key results** — Agile, robust locomotion over varied outdoor terrain including a steep unpaved trail; traverses hundreds of meters; single- and double-leg hopping; omnidirectional locomotion and recovery from large perturbations in a compact setup.

## Takeaways
- The design thesis is co-designing hardware for simulation fidelity so that a *simple* RL policy with minimal randomization transfers — inverting the usual "throw more domain randomization at a bad sim gap" approach.
- Open hardware + code (isaac_berkeley_humanoid) lowers the barrier to reproducible learning-based humanoid research.
- Demonstrates dynamic behaviors (hopping, trail walking) as evidence the platform supports genuinely agile control, not just quasi-static walking.

## Relevance to your work
A concrete, reproducible humanoid testbed for learning-based locomotion — relevant infrastructure context for deploying and benchmarking RL-plus-control locomotion policies of the kind studied in [[@compton2025dynamic]].

## Concepts
[[massively-parallel-simulation]]

## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `Liao2024`
- arXiv: https://arxiv.org/abs/2407.21781
