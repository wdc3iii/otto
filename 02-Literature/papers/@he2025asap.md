---
type: paper
citekey: he2025asap
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- He, Tairan
- Gao, Jiawei
- Xiao, Wenli
- Zhang, Yuanhang
- Wang, Zi
- Wang, Jiashun
- Luo, Zhengyi
- He, Guanqi
- Sobanbab, Nikhil
- Pan, Chaoyi
- others
year: 2025
venue: arXiv preprint arXiv:2502.01143
doi: null
arxiv: '2502.01143'
url: https://arxiv.org/abs/2502.01143
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@he2025asap.pdf
bibkeys:
- he2025asap
---

# ASAP: Aligning Simulation and Real-World Physics for Learning Agile Humanoid Whole-Body Skills

> [!info] He, Tairan; Gao, Jiawei; Xiao, Wenli; Zhang, Yuanhang; Wang, Zi; Wang, Jiashun · 2025 · arXiv preprint arXiv:2502.01143

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — ASAP is a two-stage sim-to-real framework that pre-trains humanoid motion-tracking policies in simulation on retargeted human motion, then learns a real-world delta (residual) action model to compensate the sim-to-real dynamics mismatch, unlocking agile whole-body skills on the Unitree G1.
**Problem** — Agile, coordinated whole-body humanoid motions are hard to transfer because of the dynamics mismatch between simulation and reality; SysID and domain randomization are labor-intensive or overly conservative, sacrificing agility.
**Method** — Stage 1 pre-trains motion-tracking policies in simulation from retargeted human motion data. Stage 2 deploys them, collects real-world data, and trains a delta (residual) action model that captures the dynamics mismatch; ASAP then fine-tunes the pre-trained policies with this delta model integrated into the simulator so they align with real dynamics.
**Key results** — Evaluated on IsaacGym→IsaacSim, IsaacGym→Genesis, and IsaacGym→real Unitree G1; significantly improves agility and whole-body coordination and reduces tracking error versus SysID, domain randomization, and delta-dynamics-learning baselines, enabling previously unachievable agile motions.

## Takeaways
- The core idea is learning a residual/delta action model from real data to correct the sim policy — a data-driven alternative to SysID and domain randomization.
- Directly relevant hardware: demonstrated on the Unitree G1 humanoid.
- Cross-simulator transfer experiments (IsaacGym→IsaacSim/Genesis) isolate the dynamics-gap-closing effect from real-world noise.

## Relevance to your work
A state-of-the-art sim-to-real recipe for agile whole-body humanoid skills on your exact platform (G1), and a residual-dynamics counterpoint to model-based tracking-error and hierarchical approaches such as [[@hierarchies2025motion]].

## Concepts
[[massively-parallel-simulation]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `he2025asap`
- arXiv: https://arxiv.org/abs/2502.01143
