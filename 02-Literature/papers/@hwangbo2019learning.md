---
type: paper
citekey: hwangbo2019learning
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- J. Hwangbo
- J. Lee
- A. Dosovitskiy
- D. Bellicoso
- V. Tsounis
- V. Koltun
- M. Hutter
year: 2019
venue: Science Robotics
doi: 10.1126/scirobotics.aau5872
arxiv: '1901.08652'
url: https://arxiv.org/abs/1901.08652
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@hwangbo2019learning.pdf
bibkeys:
- HutterScience19
---

# Learning agile and dynamic motor skills for legged robots

> [!info] J. Hwangbo; J. Lee; A. Dosovitskiy; D. Bellicoso; V. Tsounis; V. Koltun · 2019 · Science Robotics
> [!info]- otto authors: [[marco-hutter]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Trains a neural-network locomotion policy in simulation and transfers it to the ANYmal quadruped, achieving command tracking, faster running, and fall recovery beyond prior hand-crafted controllers.
**Problem** — Dynamic, agile legged maneuvers are extremely hard to reproduce with human-crafted control methods; a data-driven alternative is needed that requires minimal hand-engineering.
**Method** — Reinforcement learning trains a control policy in simulation, using fast, automated, and cost-effective data generation; a key ingredient is a learned actuator model that captures the real actuator dynamics so the sim-trained policy transfers (sim-to-real) to the physical ANYmal robot.
**Key results** — On hardware, ANYmal precisely and energy-efficiently follows high-level body-velocity commands, runs faster than previously achieved on the platform, and recovers from falls even from complex configurations.

## Takeaways
- Landmark sim-to-real RL result for legged robots; the learned actuator model is the crucial bridge closing the reality gap.
- RL "requires minimal craftsmanship" relative to model-based controllers — the design effort moves into simulation, reward, and actuator modeling.
- Establishes command-following, agility, and fall recovery from a single learned policy as achievable, motivating much of the subsequent legged-RL literature.

## Relevance to your work
The foundational sim-to-real RL locomotion result that later safety- and control-theoretic work (e.g. [[@cohen2025safety]]) positions itself against: it shows learned policies can outperform hand-crafted controllers on agility and recovery, motivating the effort to add formal safety/stability guarantees on top of such policies.

## Concepts


## Source
- Cited by [[@cohen2025safety]]
- bibkeys: `HutterScience19`
