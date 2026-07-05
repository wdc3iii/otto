---
type: paper
citekey: terrain2026consistent
tags: [rl, locomotion, navigation]
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors: []
year: 2026
venue: (under review)
doi: null
arxiv: null
url: null
zotero: null
status: read
mine: true
summary: ai-draft
pdf: attachments/@terrain2026consistent.pdf
---

# Terrain Consistent Reference-Guided RL for Humanoid Navigation Autonomy

> [!info] anonymized · 2026 · (under review) — **my paper**

> [!warning] Anonymized PDF — set the real authors (updates the citekey & merges cross-citations).

## Abstract
We present a method for training reference- guided, perceptive reinforcement learning locomotion policies for humanoid robots in which reference trajectories are mod- ulated in training to be consistent with terrain geometry. Aiming to deploy our method with standard navigation auton- omy infrastructure, we synthesize SE(2)-controllable reference trajectories inside the RL training loop, projecting desired footsteps onto valid footholds and adjusting swing-foot and center-of-mass trajectories to match the terrain. The resulting policy exposes a clean SE(2) velocity interface compatible with standard navigation planners. In simulation, environmentally- conditioned references significantly improve reference tracking performance compared to environment agnostic references. On hardware, we integrate the policy with an MPC + control barrier function planner and demonstrate long-horizon (>70m) closed-loop autonomous navigation on the Unitree G1 through outdoor environments containing rough terrain and consecutive flights of stairs, with all sensing and computation onboard.

## Summary
> [!note] AI-drafted from the abstract/intro — a base to refine or replace with your own framing.

**TL;DR** — Trains **perceptive, reference-guided RL** locomotion whose reference trajectories are *modulated during training to be consistent with terrain geometry*, exposing a clean SE(2) velocity interface that plugs into standard navigation planners.
**Problem** — Strong RL locomotion struggles to (a) interface with planner-issued commands and (b) condition on terrain geometry (valid footholds).
**Method** — Synthesize SE(2)-controllable reference trajectories inside the RL loop using reduced-order models; project desired footsteps onto valid footholds and adjust swing-foot/CoM to match terrain.
**Key results** — Sim: terrain-conditioned references sharply improve tracking. Hardware: integrated with an **MPC + control-barrier-function planner** for **>70 m** closed-loop autonomous navigation on a **Unitree G1** over rough terrain and stairs, fully onboard.

## Takeaways
- Shaping references to the terrain *in training* is what makes the policy planner- and perception-compatible.
- The SE(2) interface is the bridge between low-level RL locomotion and high-level navigation.

## Where it sits in my work
The navigation-autonomy capstone for the RL-locomotion line: shares the controllable-runner goal of [[@olkin2026chasing]] and pairs a [[control-barrier-function]] planner with [[reduced-order-model|ROM]]-based references.

## Concepts
- [[reduced-order-model]] · [[control-barrier-function]] · _to add:_ reference-guided-rl, navigation-autonomy

## References (in otto)
- [[@agha2022nebula]]
- [[@agrawal2017discrete]]
- [[@allshire2025visual]]
- [[@andersson2019casadi]]
- [[@benndgallant]]
- [[@cheng2024navila]]
- [[@cohen2025safety]]
- [[@compton2026lio]]
- [[@dixit2024step]]
- [[@he2025attention]]
- [[@huang2023efficient]]
- [[@jenelten2024dtc]]
- [[@lee2024asap]]
- [[@lee2024integrating]]
- [[@li2026clf]]
- [[@liao2025beyondmimic]]
- [[@lin2021long]]
- [[@liu2025opt2skill]]
- [[@long2025learning]]
- [[@mittal2025isaac]]
- [[@olkin2026chasing]]
- [[@schwarke2025rsl]]
- [[@segal2009generalized]]
- [[@sleiman2026zest]]
- [[@stereolabs2024zed]]
- [[@su2025lipm]]
- [[@wachter2006implementation]]
- [[@wangndbeamdojo]]
- [[@wu2026perceptive]]
- [[@xiongnd3d]]
- [[@xiongndglobal]]
- [[@xu2021fast]]
- [[@xu2022fast]]
- [[@yoon2025state]]
- [[@yu2022dynamic]]
- [[@zhang2026rpl]]
- [[@zhuang2024humanoid]]
