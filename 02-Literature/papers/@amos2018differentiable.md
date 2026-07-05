---
type: paper
citekey: amos2018differentiable
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Amos, Brandon
- Jimenez, Ivan
- Sacks, Jacob
- Boots, Byron
- Kolter, J Zico
year: 2018
venue: Advances in neural information processing systems
doi: null
arxiv: '1810.13400'
url: https://arxiv.org/abs/1810.13400
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@amos2018differentiable.pdf
bibkeys:
- amos2018differentiable
---

# Differentiable mpc for end-to-end planning and control

> [!info] Amos, Brandon; Jimenez, Ivan; Sacks, Jacob; Boots, Byron; Kolter, J Zico · 2018 · Advances in neural information processing systems

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Makes Model Predictive Control (MPC) a differentiable policy class, so the cost and dynamics inside the controller can be learned end-to-end by backpropagating through the optimizer.
**Problem** — MPC embeds a structured optimization prior, but coupling it to end-to-end learning requires differentiating through the control optimization, which generic neural policies sidestep at the cost of interpretability and data efficiency.
**Method** — Treats MPC as a differentiable policy for continuous state/action RL and imitation, differentiating through the controller analytically via "the KKT conditions of the convex approximation at a fixed point of the controller" (implicit differentiation at the fixed point rather than unrolling the solver).
**Key results** — On pendulum and cartpole, the MPC policies are more data-efficient than generic neural networks and outperform pure system identification when the expert's behavior is not realizable by the assumed dynamics.

## Takeaways
- Key trick: differentiate the MPC solution by implicit differentiation of the KKT system at the fixed point — cheap and avoids unrolling every solver iteration.
- Injects the MPC optimization as a structural prior into a learnable policy, buying data efficiency over unstructured nets.
- Demonstrated on low-dimensional benchmarks (pendulum, cartpole); scaling to high-DOF systems is left open.

## Relevance to your work
Differentiable MPC sits exactly at the RL/optimal-control interface you work in: it lets learned cost/dynamics be fit end-to-end while keeping an MPC layer's structure and constraints — relevant to learning-augmented model-based controllers such as those in [[@csomayshanklin2024robust]].

## Concepts


## Source
- Cited by [[@csomayshanklin2024robust]]
- bibkeys: `amos2018differentiable`
