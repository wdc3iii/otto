---
type: paper
citekey: grandia2023perceptive
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Grandia, Ruben
- Jenelten, Fabian
- Yang, Shaohui
- Farshidian, Farbod
- Hutter, Marco
year: 2023
venue: IEEE Transactions on Robotics
doi: 10.1109/TRO.2023.3275384
arxiv: 2208.08373
url: https://arxiv.org/abs/2208.08373
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@grandia2023perceptive.pdf
bibkeys:
- grandia2023perceptive
- grandia_perceptive_2023
---

# Perceptive locomotion through nonlinear model-predictive control

> [!info] Grandia, Ruben; Jenelten, Fabian; Yang, Shaohui; Farshidian, Farbod; Hutter, Marco · 2023 · IEEE Transactions on Robotics
> [!info]- otto authors: [[marco-hutter]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A complete perception-planning-control pipeline that runs whole-body nonlinear MPC in real time over perceived terrain, achieving state-of-the-art dynamic climbing on ANYmal.
**Problem** — Dynamic locomotion over rough terrain needs accurate foot placement, collision avoidance, and planning of underactuated dynamics, all under imperfect and incomplete perceptive information — hard to optimize reliably in real time.
**Method** — From an elevation map, the pipeline precomputes steppability classification, plane segmentation, and a signed distance field, then extracts a sequence of convex inequality constraints as local approximations of foothold feasibility and embeds them in an online MPC that optimizes all DOF. The nonlinear program is solved reliably and at high rate using multiple-shooting, a real-time-iteration scheme, and a filter-based line search.
**Key results** — Validated in simulation on gaps, slopes, and stepping stones, and experimentally on the ANYmal quadruped, yielding state-of-the-art dynamic climbing.

## Takeaways
- Turning terrain into convex per-foothold constraints is the key trick that keeps a hard, non-convex perceptive-locomotion problem tractable for online MPC.
- Heavy precomputation per elevation map (SDF, plane segmentation, steppability) is what buys the real-time solve rate — the perception/optimization split is deliberate.
- Whole-body real-time NMPC on hardware is feasible with RTI + multiple-shooting + filter line-search; a strong data point for MPC-based locomotion over learned/model-free approaches.

## Relevance to your work
A state-of-the-art instance of real-time nonlinear MPC for perceptive legged locomotion — the full-order optimization-based end of the planning/control design space your hierarchical work sits against. See [[@hierarchies2025motion]].

## Concepts


## Source
- Cited by [[@compton2024constructive]], [[@hierarchies2025motion]]
- bibkeys: `grandia2023perceptive`, `grandia_perceptive_2023`
