---
type: paper
citekey: wensing2024optimization
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Wensing, Patrick M.
- Posa, Michael
- Hu, Yue
- Escande, Adrien
- Mansard, Nicolas
- Prete, Andrea Del
year: 2024
venue: IEEE Transactions on Robotics
doi: 10.1109/TRO.2023.3324580
arxiv: null
url: https://doi.org/10.1109/TRO.2023.3324580
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- WensingTRO24
- wensing_optimization_2024
---

# Optimization-Based Control for Dynamic Legged Robots

> [!info] Wensing, Patrick M.; Posa, Michael; Hu, Yue; Escande, Adrien; Mansard, Nicolas; Prete, Andrea Del · 2024 · IEEE Transactions on Robotics

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A survey of model-based optimization for real-time generation and control of legged locomotion, organized around how contacts are handled, how models are simplified, and how those choices shape the numerical solvers used.
**Problem** — The community has converged on generating locomotion control by solving an optimal control problem (OCP), but solving the general OCP online is intractable due to intermittent unidirectional environmental contacts and the many degrees of freedom of legged robots.
**Method** — The survey reviews techniques that make these OCPs computationally tractable for quadrupeds, bipeds, and humanoids, with specific attention to the treatment of environmental contacts, model simplification/reduction, and the resulting numerical solution methods, while pointing toward combination with learning-based formulations.
**Key results** — A structured synthesis of the model-based optimal-control literature (a survey, not a single empirical result), mapping the design space of contact handling, model fidelity, and solver choice.

## Takeaways
- Frames real-time legged control as an online OCP whose tractability hinges on contact treatment and model simplification.
- Useful taxonomy linking modeling choices (reduced vs. full-order) to the numerical methods they admit.
- Explicitly anticipates hybridizing model-based optimization with learning — a bridge to RL-based locomotion.

## Concepts
[[reduced-order-model]]

## Relevance to your work
The canonical survey to cite when situating MPC/optimal-control-based legged locomotion — the model-based side of the model-vs-learning divide your work bridges.

## Source
- Cited by [[@cohen2025safety]], [[@olkin2026stability]]
- bibkeys: `WensingTRO24`, `wensing_optimization_2024`
- DOI: https://doi.org/10.1109/TRO.2023.3324580
