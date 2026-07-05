---
type: paper
citekey: chen2022interactive
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Chen, Yuxiao
- Rosolia, Ugo
- Ubellacker, Wyatt
- Csomay-Shanklin, Noel
- Ames, Aaron D.
year: 2022
venue: IEEE Robotics and Automation Letters
doi: 10.1109/lra.2022.3156648
arxiv: 2109.05128
url: https://arxiv.org/abs/2109.05128
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@chen2022interactive.pdf
bibkeys:
- chen_interactive_2022
---

# Interactive multi-modal motion planning with branch model predictive control

> [!info] Chen, Yuxiao; Rosolia, Ugo; Ubellacker, Wyatt; Csomay-Shanklin, Noel; Ames, Aaron D. · 2022 · IEEE Robotics and Automation Letters

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A branch Model Predictive Control framework that plans over a *tree* of feedback policies to handle the multimodal reactive behavior of uncontrolled agents.
**Problem** — Planning among uncontrolled agents (other vehicles/robots) is hard because their reactions are multimodal, injecting a discrete element into an otherwise continuous motion-planning problem.
**Method** — Builds a scenario tree from a finite set of the uncontrolled agent's candidate policies; branch MPC then solves for a feedback policy shaped as a *trajectory tree* sharing the scenario tree's topology. A coherent risk measure — Conditional Value at Risk (CVaR) — serves as a tuning knob to trade off performance against robustness.
**Key results** — Demonstrated on an autonomous-vehicle planning problem in simulation and on a hardware quadruped operating alongside an uncontrolled quadruped, producing human-like behaviors that balance safety and performance.

## Takeaways
- Scenario-tree / trajectory-tree branch MPC keeps a continuous plan per mode instead of committing to one prediction — contingency planning over feedback policies.
- CVaR gives a principled, tunable risk-vs-performance dial rather than worst-case-only robustness.
- Validated on real quadruped hardware, not just simulation.

## Relevance to your work
Contingency/branch MPC over feedback policies is directly relevant to reactive, interactive locomotion planning around other agents; [[@hierarchies2025motion]] cites it as an approach to multimodal reactive planning within a layered stack.

## Concepts

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `chen_interactive_2022`
