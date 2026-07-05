---
type: paper
citekey: yoon2025state
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Yoon, Ziwon
- Zhu, Lawrence Y
- Lu, Jingxi
- Gan, Lu
- Zhao, Ye
year: 2025
venue: IEEE Robotics and Automation Letters
doi: null
arxiv: '2506.01046'
url: https://arxiv.org/abs/2506.01046
summary: ai-draft
pdf: attachments/@yoon2025state.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- yoon2025state
---

# STATE-NAV: Stability-Aware Traversability Estimation for Bipedal Navigation on Rough Terrain

> [!info] Yoon, Ziwon; Zhu, Lawrence Y; Lu, Jingxi; Gan, Lu; Zhao, Ye · 2025 · IEEE Robotics and Automation Letters

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — A learning-based, stability-aware traversability estimator and risk-sensitive planner for bipedal navigation on rough terrain, integrating a learned instability predictor into an RRT*/MPC hierarchy.

**Problem** — Bipeds fail more readily than wheeled/quadrupedal platforms, yet bipedal traversability has relied on hand-designed rules that largely ignore locomotion stability on uneven terrain; learned traversability was under-explored for bipeds.

**Method** — TravFormer, a transformer network, predicts bipedal instability with uncertainty, enabling risk-aware planning. Traversability is defined as a stability-aware command velocity — the fastest command velocity that keeps predicted instability below a user-defined limit. This velocity-based traversability feeds a hierarchical planner combining traversability-informed RRT* (TravRRT*) for time-efficient global planning with MPC for safe execution.

**Key results** — Validated in MuJoCo and the real world, showing improved navigation with better robustness and time efficiency across varying terrains versus existing methods.

## Takeaways
- Recasts "traversability" as a stability-aware command velocity rather than a binary cost — a locomotion-grounded, risk-tunable notion.
- Uncertainty-aware instability prediction (TravFormer) lets the planner be explicitly risk-sensitive via a user-defined instability limit.
- Two-layer planner: TravRRT* for global routing, MPC for safe local execution.

## Relevance to your work
Directly in the humanoid/bipedal navigation-autonomy space: it couples a learned stability model to a hierarchical planner, a close companion to reference-guided terrain-aware navigation like [[@terrain2026consistent]].

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `yoon2025state`
