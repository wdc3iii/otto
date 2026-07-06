---
type: paper
citekey: olkin2025chasing
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Olkin, Zachary
- Li, Kejun
- Compton, William D.
- Ames, Aaron D.
year: 2025
venue: arXiv
doi: 10.48550/arXiv.2509.19573
arxiv: '2509.19573'
url: https://arxiv.org/abs/2509.19573
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@olkin2025chasing.pdf
bibkeys:
- olkin_chasing_2025
---

# Chasing Stability: Humanoid Running via Control Lyapunov Function Guided Reinforcement Learning

> [!info] Olkin, Zachary; Li, Kejun; Compton, William D.; Ames, Aaron D. · 2025 · arXiv
> [!info]- otto authors: [[aaron-ames]] · [[zachary-olkin]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — CLF-RL embeds control Lyapunov functions and optimized dynamic reference trajectories into the RL reward, yielding certifiable-stability-oriented, heuristic-free humanoid running with real flight and single-support phases.
**Problem** — Highly dynamic humanoid behaviors like running need controllers that are simultaneously robust and precise; classical synthesis for nonlinear/hybrid dynamics is hard, while pure RL relies on brittle hand-tuned reward heuristics.
**Method** — The approach (CLF-RL) shapes the RL reward using a control Lyapunov function together with optimized dynamic reference trajectories, replacing handcrafted heuristic reward terms. Grounding policy learning in dynamically feasible references encourages certifiable stability, provides meaningful intermediate rewards, and expands the robot's dynamic envelope to include flight and single-support running phases.
**Key results** — The learned policy runs reliably on a treadmill and outdoors, is robust to disturbances applied to the torso and feet, and achieves accurate global reference tracking using only on-board sensors.

## Takeaways
- CLF-derived reward shaping removes most reward-term hand-tuning while pushing toward provable stability.
- Optimized dynamic reference trajectories give dense, physically grounded intermediate rewards, enabling flight-phase running.
- On-board-only accurate global tracking is framed as a step toward folding dynamic running into a full autonomy stack.

## Abstract (from bib)
Achieving highly dynamic behaviors on humanoid robots, such as running, requires controllers that are both robust and precise, and hence difficult to design. Classical control methods offer valuable insight into how such systems can stabilize themselves, but synthesizing real-time controllers for nonlinear and hybrid dynamics remains challenging. Recently, reinforcement learning (RL) has gained popularity for locomotion control due to its ability to handle these complex dynamics. In this work, we embed ideas from nonlinear control theory, specifically control Lyapunov functions (CLFs), along with optimized dynamic reference trajectories into the reinforcement learning training process to shape the reward. This approach, CLF-RL, eliminates the need to handcraft and tune heuristic reward ter

## Concepts


## Relevance to your work
Directly in your CLF-RL line: it fuses Lyapunov-based stability certificates with RL reward shaping for dynamic humanoid running, the precursor synthesized further in [[@olkin2026stability]].

## Source
- Cited by [[@olkin2026stability]]
- bibkeys: `olkin_chasing_2025`
- DOI: https://doi.org/10.48550/arXiv.2509.19573
