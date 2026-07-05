---
type: paper
citekey: benders2024embedded
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- D. Benders
- J. K\"ohlher
- T. Niesten
- R. Bab\uuska
- J. Alonso-Mora
- L. Ferranti
year: 2024
venue: arXiv preprint arXiv:2406.11506
doi: 10.1109/tro.2025.3567529
arxiv: '2406.11506'
url: https://arxiv.org/abs/2406.11506
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@benders2024embedded.pdf
bibkeys:
- BendersArXiv24
---

# Embedded Hierarchical MPC for Autonomous Navigation

> [!info] D. Benders; J. K\"ohlher; T. Niesten; R. Bab\uuska; J. Alonso-Mora; L. Ferranti · 2024 · arXiv preprint arXiv:2406.11506

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A two-layer nonlinear MPC that runs a slow, long-horizon planner above a fast tracker so full MPC-based navigation becomes real-time feasible on compute-limited embedded robots.
**Problem** — Nonlinear MPC gives dynamically feasible, collision-free trajectories, but its most expensive steps (constraint generation and optimization) are hard to run in real time on the limited hardware of platforms like quadrotors.
**Method** — A hierarchical MPC scheme splits the work: a planning layer constructs a trajectory with a long prediction horizon at a slow rate, while a tracking layer ensures the robot follows that trajectory at a relatively fast rate. The decomposition keeps each layer's per-cycle optimization cheap enough for embedded deployment.
**Key results** — Demonstrates real-time hierarchical MPC navigation on embedded robotic hardware; later published in IEEE T-RO (2025).

## Takeaways
- Planner/tracker split is the lever: long horizon where it matters (planning, slow) and fast feedback where it matters (tracking), rather than one monolithic MPC.
- Targets the embedded-compute bottleneck directly — constraint generation and optimization cost is the thing being amortized across the two rates.
- The guarantee story hinges on the tracker staying close to the planned trajectory; that coupling is the assumption to scrutinize.

## Relevance to your work
A concrete embedded realization of the planner/tracker hierarchy you study in [[@hierarchies2025motion]]: it shows the two-rate decomposition making nonlinear MPC tractable on real hardware, which is exactly the setting where certified tracking-error bounds between layers earn their keep.

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@cohen2025safety]]
- bibkeys: `BendersArXiv24`
- arXiv: https://arxiv.org/abs/2406.11506
