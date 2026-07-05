---
type: paper
citekey: wensing2023optimization
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Wensing, Patrick M
- Posa, Michael
- Hu, Yue
- Escande, Adrien
- Mansard, Nicolas
- Del Prete, Andrea
year: 2023
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
- wensing2022optimizationbasedcontroldynamiclegged
- wensing2023optimization
---

# Optimization-based control for dynamic legged robots

> [!info] Wensing, Patrick M; Posa, Michael; Hu, Yue; Escande, Adrien; Mansard, Nicolas; Del Prete, Andrea · 2023 · IEEE Transactions on Robotics

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A survey of model-based optimization for real-time generation and control of legged locomotion, organized around how contacts are treated, how models are simplified, and how those choices shape the numerical solvers used.
**Problem** — Most locomotion controllers reduce to solving an optimal control problem (OCP), but the fully general OCP is intractable online because of intermittent unidirectional environmental contacts and the many degrees of freedom of legged robots.
**Method** — The survey catalogs the techniques that make these OCPs tractable, grouping the design space along three axes: contact treatment (e.g., hybrid/complementarity vs. predefined schedules), model fidelity/simplification (full-order vs. reduced/template models), and the resulting numerical solution methods. It emphasizes model-based optimization while pointing toward combination with learning-based formulations.
**Key results** — A structured, cross-cutting map of optimization-based locomotion control rather than a single new method; a reference framework connecting contact modeling, model reduction, and solver choice.

## Takeaways
- The central tension is tractability vs. fidelity: how you model contact and how much you simplify the dynamics dictates which solver is viable online.
- Reduced/template models are one of the primary levers for real-time feasibility.
- Explicitly frames model-based optimization as complementary to (not competing with) learning-based control — a useful lens for hybrid RL+MPC stacks.

## Relevance to your work
The definitive recent survey framing optimization-based legged control and the role of model reduction — directly relevant context for robust/reduced-order MPC locomotion work such as [[@csomayshanklin2024robust]].

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@csomayshanklin2024robust]], [[@hierarchies2025motion]]
- bibkeys: `wensing2022optimizationbasedcontroldynamiclegged`, `wensing2023optimization`
