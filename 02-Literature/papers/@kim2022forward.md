---
type: paper
citekey: kim2022forward
tags: [navigation, planning, rl]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Kim, Yunho
- Kim, Chanyoung
- Hwangbo, Jemin
year: 2022
venue: arXiv
doi: 10.48550/arXiv.2204.08647
arxiv: '2204.08647'
url: http://arxiv.org/abs/2204.08647
zotero: null
summary: ai-draft
pdf: attachments/@kim2022forward.pdf
status: to-read
mine: false
bibkeys:
- kimLearningForwardDynamics2022
---

# Learning Forward Dynamics Model and Informed Trajectory Sampler for Safe Quadruped Navigation

> [!info] Yunho Kim; Chanyoung Kim; Jemin Hwangbo · 2022 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A learned forward dynamics model plus an online sampling-based MPC and an informed trajectory sampler builds a safe, collision-free local planner that tracks a coarse global path in complex, narrow environments.
**Problem** — In hierarchical quadruped navigation (mapper / global planner / local planner / command-tracking controller), waypoint-based local planners (PD, pure pursuit) collide frequently in geometrically complex, narrow spaces because the global planner uses a coarse, inaccurate model and the local planner tracks it poorly; existing deep-learning methods can't plan over a long horizon.
**Method** — A learning-based fully autonomous framework with three parts: a learned forward dynamics model (FDM), an online sampling-based model-predictive controller, and an informed trajectory sampler (ITS) to generate the velocity plan tracking the global path.
**Key results** — Navigates diverse complex environments collision-free with smoother command plans than the baseline, and reactively avoids unexpected obstacles on the planned path (no numeric figures read).

## Takeaways
- Learned FDM gives an accurate short-horizon predictor to close the model-fidelity gap between coarse global plan and reality.
- Informed trajectory sampler focuses sampling-based MPC, enabling longer effective horizons than prior deep methods.
- Reactive handling of unexpected obstacles comes for free from the online re-planning MPC loop.

## Relevance to your work
Learned-dynamics + sampling MPC as a safe local planner sits alongside your tube-MPC / reduced-order-model interests, and the coarse-global-vs-accurate-local-model gap is exactly the capability-awareness problem in the navigation stack you care about for the G1.

## Abstract (from bib)
For autonomous quadruped robot navigation in various complex environments, a typical SOTA system is composed of four main modules -- mapper, global planner, local planner, and command-tracking controller -- in a hierarchical manner. In this paper, we build a robust and safe local planner which is designed to generate a velocity plan to track a coarsely planned path from the global planner. Previous works used waypoint-based methods (e.g. Proportional-Differential control and pure pursuit) which simplify the path tracking problem to local point-goal navigation. However, they suffer from frequent collisions in geometrically complex and narrow environments because of two reasons; the global planner uses a coarse and inaccurate model and the local planner is unable to track the global plan sufficiently well. Currently, deep learning methods are an appealing alternative because they can learn safety and path feasibility from experience more accurately. However, existing deep learning methods are not capable of planning for a long horizon. In this work, we propose a learning-based fully autonomous navigation framework composed of three innovative elements: a learned forward dynamics model (FDM), an online sampling-based model-predictive controller, and an informed trajectory sampler (ITS). Using our framework, a quadruped robot can autonomously navigate in various complex environments without a collision and generate a smoother command plan compared to the baseline method. Furthermore, our method can reactively handle unexpected obstacles on the planned path and avoid them. Project page https://awesomericky.github.io/projects/FDM\_ITS\_navigation/.

## Concepts
- [[forward-dynamics-model]]
- [[hierarchical-control]]
- [[capability-awareness]]

## Source
- bibkeys: `kimLearningForwardDynamics2022`
- arXiv: http://arxiv.org/abs/2204.08647
- DOI: https://doi.org/10.48550/arXiv.2204.08647
- URL: http://arxiv.org/abs/2204.08647
