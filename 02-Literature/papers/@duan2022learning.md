---
type: paper
citekey: duan2022learning
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Duan, Helei
- Malik, Ashish
- Gadde, Mohitvishnu S.
- Dao, Jeremy
- Fern, Alan
- Hurst, Jonathan
year: 2022
venue: 2022 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)
doi: 10.1109/IROS47612.2022.9981884
arxiv: null
url: https://doi.org/10.1109/IROS47612.2022.9981884
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- duan_learning_2022
---

# Learning Dynamic Bipedal Walking Across Stepping Stones

> [!info] Duan, Helei; Malik, Ashish; Gadde, Mohitvishnu S.; Dao, Jeremy; Fern, Alan; Hurst, Jonathan · 2022 · 2022 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — An RL approach plus a learned feasibility model that enables closed-loop, perception-in-the-loop dynamic bipedal walking across stepping stones on the real Cassie robot.
**Problem** — Prior stepping-stone demonstrations were largely simple, open-loop, and perception-free; achieving closed-loop dynamic walking over real stepping-stone patterns remained open.
**Method** — First trains, via RL in simulation, a controller that maps footstep commands to joint actions with no reference-motion information. Then learns a model of that controller's capabilities to predict which footsteps are feasible from the robot's current dynamic state. Controller and feasibility model are integrated with a real-time overhead camera detecting stepping-stone locations.
**Key results** — Demonstrates closed-loop dynamic walking over moderately difficult stepping-stone patterns in both simulation and the real world, evaluated on a purpose-built benchmark set of patterns (no numeric metrics seen).

## Takeaways
- Pairs a reference-free RL footstep-tracking controller with a learned feasibility/capability model — the model turns raw commands into achievable footholds.
- Closed-loop with real perception (overhead camera) is the key advance over earlier open-loop stepping-stone demos.
- Introduces a benchmark set of stepping-stone patterns for repeatable evaluation.

## Relevance to your work
A learning-based, perception-in-the-loop take on foothold-constrained dynamic walking, cited by [[@dai2025walk]] alongside model-based methods for walking across constrained footholds.

## Abstract (from bib)
In this work, we propose a learning approach for 3D dynamic bipedal walking when footsteps are constrained to stepping stones. While recent work has shown progress on this problem, real-world demonstrations have been limited to relatively simple open-loop, perception-free scenarios. Our main contribution is a more advanced learning approach that enables real-world demonstrations, using the Cassie robot, of closed-loop dynamic walking over moderately difficult stepping-stone patterns. Our approach first uses reinforcement learning (RL) in simulation to train a controller that maps footstep commands onto joint actions without any reference motion information. We then learn a model of that controller's capabilities, which enables prediction of feasible footsteps given the robot's current dyna

## Concepts

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `duan_learning_2022`
- DOI: https://doi.org/10.1109/IROS47612.2022.9981884
