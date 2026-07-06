---
type: paper
citekey: li2025clf
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Li, Kejun
- Olkin, Zachary
- Yue, Yisong
- Ames, Aaron D.
year: 2025
venue: arXiv:2508.09354 [cs]
doi: 10.48550/arXiv.2508.09354
arxiv: '2508.09354'
url: https://arxiv.org/abs/2508.09354
summary: ai-draft
pdf: attachments/@li2025clf.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- li_clf-rl_2025
---

# CLF-RL: Control Lyapunov Function Guided Reinforcement Learning

> [!info] Li, Kejun; Olkin, Zachary; Yue, Yisong; Ames, Aaron D. · 2025 · arXiv:2508.09354 [cs]
> [!info]- otto authors: [[aaron-ames]] · [[zachary-olkin]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Use model-based reference trajectories and control Lyapunov functions to shape RL rewards, yielding robust, lightweight bipedal locomotion policies deployed on the Unitree G1.
**Problem** — RL locomotion policies are effective but suffer from tedious reward design and sensitivity to poorly shaped objectives.
**Method** — A structured reward-shaping framework generates reference trajectories from two model-based planners — a reduced-order LIP model for velocity-conditioned planning and a precomputed HZD full-order gait library — and constructs CLF-based rewards that penalize tracking error and encourage rapid convergence. Both the references and CLF shaping are used only during training, so the deployed policy stays lightweight.
**Key results** — Validated in simulation and extensive real-world Unitree G1 experiments; CLF-RL shows markedly improved robustness over a baseline RL policy and outperforms a classic tracking-reward RL formulation.

## Takeaways
- CLFs enter as a *reward-shaping signal* during training, not as a runtime QP constraint — a distinctive way to inject model-based structure into model-free RL.
- Two reference sources (reduced-order LIP vs. full-order HZD gait library) offer a knob between velocity-conditioned flexibility and precise full-order fidelity.
- References and CLF shaping are training-only, keeping deployment cheap while retaining robustness gains — key for onboard humanoid use.

## Abstract (from bib)
Reinforcement learning (RL) has shown promise in generating robust locomotion policies for bipedal robots, but often suffers from tedious reward design and sensitivity to poorly shaped objectives. In this work, we propose a structured reward shaping framework that leverages model-based trajectory generation and control Lyapunov functions (CLFs) to guide policy learning. We explore two model-based planners for generating reference trajectories: a reduced-order linear inverted pendulum (LIP) model for velocity-conditioned motion planning, and a precomputed gait library based on hybrid zero dynamics (HZD) using full-order dynamics. These planners define desired end-effector and joint trajectories, which are used to construct CLF-based rewards that penalize tracking error and encourage rapid c

## Relevance to your work
A control/RL/locomotion researcher cites this for the CLF-as-reward-shaping idea that fuses classical Lyapunov structure with RL on real humanoid hardware; directly adjacent to learning-based G1 locomotion in [[@dai2025walk]].

## Concepts
[[reduced-order-model]] [[tracking-error-bound]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `li_clf-rl_2025`
- arXiv: https://arxiv.org/abs/2508.09354
- DOI: https://doi.org/10.48550/arXiv.2508.09354
