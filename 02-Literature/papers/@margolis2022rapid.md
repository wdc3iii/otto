---
type: paper
citekey: margolis2022rapid
tags: [locomotion, rl]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Margolis, Gabriel B.
- Yang, Ge
- Paigwar, Kartik
- Chen, Tao
- Agrawal, Pulkit
year: 2022
venue: arXiv
doi: 10.48550/arXiv.2205.02824
arxiv: '2205.02824'
url: http://arxiv.org/abs/2205.02824
zotero: null
summary: ai-draft
pdf: attachments/@margolis2022rapid.pdf
status: to-read
mine: false
bibkeys:
- margolisRapidLocomotionReinforcement2022
---

# Rapid Locomotion via Reinforcement Learning

> [!info] Gabriel B. Margolis; Ge Yang; Kartik Paigwar; Tao Chen; Pulkit Agrawal · 2022 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — An end-to-end RL controller trained in sim and transferred to the MIT Mini Cheetah achieves record agility, sustaining speeds up to 3.9 m/s across natural terrains.
**Problem** — Agile maneuvers like sprinting and high-speed turning in the wild are hard for legged robots.
**Method** — A neural-network controller trained in simulation via RL and transferred to hardware, built on two key components: (i) an adaptive curriculum on velocity commands and (ii) an online system-identification strategy for sim-to-real (leveraged from prior work).
**Key results** — Record agility for the MIT Mini Cheetah with sustained speeds up to 3.9 m/s; runs and turns fast on grass, ice, and gravel and responds robustly to disturbances.

## Takeaways
- Adaptive velocity-command curriculum is central to unlocking high-speed agility.
- Online system identification supports robust sim-to-real transfer.
- Demonstrates robustness across varied natural terrains and to disturbances.

## Relevance to your work
Core reference for your RL-locomotion line: the adaptive command curriculum + online sysID recipe is a canonical high-speed sim-to-real approach for legged robots, directly informing velocity-tracking policy design and transfer for humanoid/quadruped locomotion.

## Abstract (from bib)
Agile maneuvers such as sprinting and high-speed turning in the wild are challenging for legged robots. We present an end-to-end learned controller that achieves record agility for the MIT Mini Cheetah, sustaining speeds up to 3.9 m/s. This system runs and turns fast on natural terrains like grass, ice, and gravel and responds robustly to disturbances. Our controller is a neural network trained in simulation via reinforcement learning and transferred to the real world. The two key components are (i) an adaptive curriculum on velocity commands and (ii) an online system identification strategy for sim-to-real transfer leveraged from prior work. Videos of the robot's behaviors are available at: https://agility.csail.mit.edu/

## Concepts
- [[rl-for-legged-locomotion]]
- [[sim-to-real-transfer]]

## Source
- bibkeys: `margolisRapidLocomotionReinforcement2022`
- arXiv: http://arxiv.org/abs/2205.02824
- DOI: https://doi.org/10.48550/arXiv.2205.02824
- URL: http://arxiv.org/abs/2205.02824
