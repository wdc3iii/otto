---
type: paper
citekey: tassa2014limited
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Tassa, Yuval
- Mansard, Nicolas
- Todorov, Emo
year: 2014
venue: 2014 ICRA
doi: 10.1109/ICRA.2014.6907001
arxiv: null
url: https://doi.org/10.1109/ICRA.2014.6907001
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- tassa2014control
---

# Control-limited differential dynamic programming

> [!info] Tassa, Yuval; Mansard, Nicolas; Todorov, Emo · 2014 · 2014 ICRA

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Generalizes Differential Dynamic Programming (DDP) to handle box inequality constraints on the controls, enabling fast trajectory optimization that respects actuator limits.
**Problem** — DDP optimizes over the unconstrained control space and is fast enough for real-time humanoid control, but control (actuator) limits break it; naive fixes like clamping or penalizing inputs are shown to be inefficient in general.
**Method** — The authors derive a control-limited DDP that solves a box-constrained quadratic program at each backward-pass step to enforce control bounds, preserving DDP's convergence quality and computational efficiency without a significant penalty.
**Key results** — Demonstrated on three simulated problems, including the 36-DoF HRP-2 humanoid, showing box control constraints handled within real-time-capable trajectory optimization.

## Takeaways
- The core contribution is a box-QP in the DDP backward pass, giving principled control-limit handling that beats clamping/penalty heuristics.
- Retains DDP's speed and second-order convergence, which is why it scales to full humanoid (36-DoF) trajectory optimization.
- Handles control limits but not general state constraints; results are in simulation.

## Relevance to your work
A workhorse trajectory-optimization method for legged/humanoid systems: control-limited DDP is a standard tool for generating dynamically-feasible, actuator-respecting motions in the planning layers you study, e.g. [[@hierarchies2025motion]].

## Concepts


## Source
- Cited by [[@csomayshanklin2024robust]], [[@hierarchies2025motion]]
- bibkeys: `tassa2014control`
