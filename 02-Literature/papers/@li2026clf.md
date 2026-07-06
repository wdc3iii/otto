---
type: paper
citekey: li2026clf
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Li, Kejun
- Olkin, Zachary
- Yue, Yisong
- Ames, Aaron D.
year: 2026
venue: IEEE Robotics and Automation Letters
doi: 10.1109/LRA.2026.3653329
arxiv: null
url: https://doi.org/10.1109/LRA.2026.3653329
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- li2026clf
- li_clf-rl_2026
---

# CLF-RL: Control Lyapunov Function Guided Reinforcement Learning

> [!info] Li, Kejun; Olkin, Zachary; Yue, Yisong; Ames, Aaron D. · 2026 · IEEE Robotics and Automation Letters
> [!info]- otto authors: [[aaron-ames]] · [[zachary-olkin]]

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — CLF-RL uses model-based reference trajectories and control Lyapunov functions to shape RL rewards, yielding more robust bipedal locomotion with less reward tuning; validated on a Unitree G1.
**Problem** — RL locomotion policies need tedious reward engineering and are sensitive to poorly shaped objectives.
**Method** — Two model-based planners generate references — a reduced-order LIP model for velocity-conditioned motion and a precomputed HZD gait library from full-order dynamics — defining desired end-effector/joint trajectories. CLF-based rewards then penalize tracking error and encourage rapid convergence, providing dense intermediate signal. References and CLF shaping are used only during training, so the deployed policy is lightweight.
**Key results** — In simulation and extensive Unitree G1 hardware experiments, CLF-RL is significantly more robust than a baseline RL policy and outperforms a classic tracking-reward RL formulation.

## Takeaways
- CLF shaping supplies dense, principled intermediate rewards without adding deployment-time cost (training-only).
- Bridges model-based planning (LIP / HZD gait library) with RL, rather than choosing one.
- Robustness and performance gains demonstrated on real G1 hardware, not just simulation.

## Relevance to your work
Directly on your line of work — CLF-guided RL for humanoid locomotion on the G1, combining reduced-order planning with learned policies. See [[@olkin2026stability]].

## Abstract (from bib)
Reinforcement learning (RL) has shown promise in generating robust locomotion policies for bipedal robots, but often suffers from tedious reward design and sensitivity to poorly shaped objectives. In this work, we propose a structured reward shaping framework that leverages model-based trajectory generation and control Lyapunov functions (CLFs) to guide policy learning. We explore two model-based planners for generating reference trajectories: a reduced-order linear inverted pendulum (LIP) model for velocity-conditioned motion planning, and a precomputed gait library based on hybrid zero dynamics (HZD) using full-order dynamics. These planners deﬁne desired end-effector and joint trajectories, which are used to construct CLF-based rewards that penalize tracking error and encourage rapid co

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@olkin2026stability]], [[@terrain2026consistent]]
- bibkeys: `li2026clf`, `li_clf-rl_2026`
- DOI: https://doi.org/10.1109/LRA.2026.3653329
