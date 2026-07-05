---
type: paper
citekey: terrain2026consistent
tags: []
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
---

# Terrain Consistent Reference-Guided RL for Humanoid Navigation Autonomy

> [!info] anonymized · 2026 · (under review) — **my paper**

> [!warning] Anonymized PDF — set the real authors (updates the citekey & merges cross-citations).

## Abstract
We present a method for training reference- guided, perceptive reinforcement learning locomotion policies for humanoid robots in which reference trajectories are mod- ulated in training to be consistent with terrain geometry. Aiming to deploy our method with standard navigation auton- omy infrastructure, we synthesize SE(2)-controllable reference trajectories inside the RL training loop, projecting desired footsteps onto valid footholds and adjusting swing-foot and center-of-mass trajectories to match the terrain. The resulting policy exposes a clean SE(2) velocity interface compatible with standard navigation planners. In simulation, environmentally- conditioned references significantly improve reference tracking performance compared to environment agnostic references. On hardware, we integrate the policy with an MPC + control barrier function planner and demonstrate long-horizon (>70m) closed-loop autonomous navigation on the Unitree G1 through outdoor environments containing rough terrain and consecutive flights of stairs, with all sensing and computation onboard.

## Summary
> [!note] Your paper — add your framing / key contribution in your own words.

## Concepts
<!-- [[03-Concepts]] links -->

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
