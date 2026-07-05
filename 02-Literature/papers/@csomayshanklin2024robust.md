---
type: paper
citekey: csomayshanklin2024robust
tags: [control, locomotion]
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Csomay-Shanklin, Noel
- Compton, William D.
- Rodriguez, Ivan D. J.
- Ambrose, Eric R.
- Yue, Yisong
- Ames, Aaron D.
year: 2024
venue: IROS 2024
doi: null
arxiv: null
url: null
zotero: null
status: read
mine: true
summary: ai-draft
pdf: attachments/@csomayshanklin2024robust.pdf
---

# Robust Agility via Learned Zero Dynamics Policies

> [!info] Csomay-Shanklin, Noel; Compton, William D.; Rodriguez, Ivan D. J.; Ambrose, Eric R.; Yue, Yisong; Ames, Aaron D. · 2024 · IROS 2024 — **my paper**

## Abstract
We study the design of robust and agile controllers for hybrid underactuated systems. Our approach breaks down the task of creating a stabilizing controller into: 1) learning a mapping that is invariant under optimal control, and 2) driving the actuated coordinates to the output of that mapping. This ap- proach, termed Zero Dynamics Policies, exploits the structure of underactuation by restricting the inputs of the target mapping to the subset of degrees of freedom that cannot be directly actuated, thereby achieving significant dimension reduction. Furthermore, we retain the stability and constraint satisfaction of optimal control while reducing the online computational overhead. We prove that controllers of this type stabilize hybrid underactuated systems and experimentally validate our ap- proach on the 3D hopping platform, ARCHER. Over the course of 3000 hops the proposed framework demonstrates robust agility, maintaining stable hopping while rejecting disturbances on rough terrain.

## Summary
> [!note] AI-drafted from the abstract/intro — a base to refine or replace with your own framing.

**TL;DR** — The robust, hardware-validated realization of **Zero Dynamics Policies**: learn a mapping invariant under optimal control, then drive the actuated coordinates to its output — stabilizing hybrid underactuated systems with far less online compute than full MPC.
**Problem** — Optimal control (MPC) for underactuated hybrid systems is expensive online; longer horizons/finer discretization fight real-time limits.
**Method** — Restrict the target map's inputs to the un-actuatable DOF (large dimension reduction); retain the stability + constraint satisfaction of optimal control while moving the cost offline. Proves stabilization of hybrid underactuated systems.
**Key results** — On the ARCHER 3D hopper, **~3000 hops** of robust agile hopping, rejecting disturbances on rough terrain.

## Takeaways
- ZDPs = an offline optimal-control map + cheap online tracking → MPC-quality behavior at a fraction of the compute.
- Demonstrates the zero-dynamics idea survives hybrid dynamics and real hardware.

## Where it sits in my work
The hardware/robust counterpart to the theory in [[@compton2024constructive]]; ARCHER is also the platform for [[@compton2025dynamic|DTMPC]] and [[@compton2025learning|predictive CBFs]].

## Concepts
- [[reduced-order-model]] · _to add:_ zero-dynamics-policy, model-predictive-control, hybrid-zero-dynamics

## References (in otto)
- [[@ambrose2022creating]]
- [[@ames2017hybrid]]
- [[@amos2017optnet]]
- [[@amos2018differentiable]]
- [[@borrelli2017predictive]]
- [[@bradbury2018jax]]
- [[@code2024x]]
- [[@compton2024constructive]]
- [[@csomayshanklin2022multi]]
- [[@csomayshanklin2023nonlinear]]
- [[@da2019combining]]
- [[@deray2020manif]]
- [[@han20223d]]
- [[@isidori1995elementary]]
- [[@kajita20013d]]
- [[@khazoom2024tailoring]]
- [[@li2024cafe]]
- [[@li2024reinforcement]]
- [[@liberzon2012calculus]]
- [[@mayne2000constrained]]
- [[@miki2022learning]]
- [[@raibert1984experiments]]
- [[@reher2021dynamic]]
- [[@reher2021lyapunov]]
- [[@rodriguez2022neural]]
- [[@sastry1999linearization]]
- [[@schulman2016high]]
- [[@suh2022do]]
- [[@supplementalndvideo]]
- [[@tassa2014limited]]
- [[@wensing2023optimization]]
- [[@westervelt2003hybrid]]
