---
type: paper
citekey: pezzato2023sampling
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Pezzato, Corrado
- Salmi, Chadi
- Spahn, Max
- Trevisan, Elia
- Alonso-Mora, Javier
- Corbato, Carlos Hern\'andez
year: 2023
venue: arXiv preprint arXiv:2307.09105
doi: 10.1109/LRA.2025.3535185
arxiv: '2307.09105'
url: https://arxiv.org/abs/2307.09105
summary: ai-draft
pdf: attachments/@pezzato2023sampling.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- pezzato2023samplingbased
---

# Sampling-based model predictive control leveraging parallelizable physics simulations

> [!info] Pezzato, Corrado; Salmi, Chadi; Spahn, Max; Trevisan, Elia; Alonso-Mora, Javier; Corbato, Carlos Hern\'andez · 2023 · arXiv preprint arXiv:2307.09105

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A sampling-based MPC (MPPI) that uses a GPU-parallelizable physics simulator (Isaac Gym) directly as its dynamics model, making it trivially extendable to new robots, objects, and contact-rich tasks.

**Problem** — Sampling-based MPC needs many forward rollouts of a dynamics model; writing task-specific analytic models is laborious and struggles with contact-rich, high-dimensional problems.

**Method** — Formulate a Model Predictive Path Integral (MPPI) controller whose forward dynamics are computed by rolling out the GPU-parallelizable IsaacGym simulator across sampled control sequences. Because the simulator implicitly defines the model, the same controller transfers across objects and robots without re-deriving dynamics.

**Key results** — Demonstrated in simulation and the real world on mobile navigation with collision avoidance, non-prehensile manipulation, and whole-body control for high-dimensional configurations; released as an open-source tool.

## Takeaways
- Using a general physics simulator as the MPC model trades analytic modeling effort for GPU-parallel sampling — a flexible, contact-agnostic recipe.
- Naturally handles high-dimensional whole-body and contact-rich tasks where gradient-based MPC with hand-derived models struggles.
- Real-time feasibility hinges on GPU-parallel rollouts (many samples in parallel); performance is bounded by simulator fidelity and sample count.

## Relevance to your work
This is the sampling-MPC counterpart to your GPU-parallel-simulation approach: it uses massively parallel rollouts to sidestep analytic dynamics for contact-rich whole-body control, a directly relevant baseline/tooling reference for [[@compton2025dynamic]].

## Concepts
[[massively-parallel-simulation]]

## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `pezzato2023samplingbased`
- arXiv: https://arxiv.org/abs/2307.09105
