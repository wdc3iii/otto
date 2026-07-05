---
type: paper
citekey: dixit2025step
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Dixit, Anushri
- Fan, David D.
- Otsu, Kyohei
- Dey, Sharmita
- Agha-Mohammadi, Ali-Akbar
- Burdick, Joel W.
year: 2025
venue: IEEE Transactions on Field Robotics
doi: 10.1109/TFR.2024.3512433
arxiv: 2303.01614
url: https://arxiv.org/abs/2303.01614
zotero: null
summary: ai-draft
pdf: attachments/@dixit2025step.pdf
status: to-read
mine: false
bibkeys:
- DARPA_Caltech
---

# STEP: Stochastic Traversability Evaluation and Planning for Risk-Aware Navigation; Results From the DARPA Subterranean Challenge

> [!info] Dixit, Anushri; Fan, David D.; Otsu, Kyohei; Dey, Sharmita; Agha-Mohammadi, Ali-Akbar; Burdick, Joel W. · 2025 · IEEE Transactions on Field Robotics

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — STEP is a risk-aware traversability-evaluation and motion-planning framework for autonomous ground navigation in unknown, perceptually degraded subterranean environments, validated across the DARPA Subterranean Challenge.
**Problem** — Robotic autonomy in extreme, off-road, unstructured, and completely unknown terrain (caves, mines, rubble, post-disaster sites) remains hard, especially under perceptual degradation.
**Method** — Combines (1) rapid uncertainty-aware mapping and traversability evaluation, (2) tail-risk assessment via conditional value-at-risk (CVaR), (3) risk- and constraint-aware kinodynamic motion planning using SQP-based model predictive control, (4) fast recovery behaviors, and (5) risk-based gait adaptation for quadrupeds.
**Key results** — Field-validated on both wheeled and legged platforms at cave, mine, and the final DARPA SubT competition sites (tunnel/urban/cave).

## Takeaways
- Treats traversability as a distribution and plans against its tail (CVaR) rather than the mean — risk-aware navigation, not just obstacle avoidance.
- Whole-stack: mapping, planning (MPC/SQP), recovery, and gait adaptation, demonstrated on real hardware in competition conditions.

## Relevance to your work
Cited in [[@hierarchies2025motion]] as an example of terrain-aware, risk-based planning layered on top of a lower-level MPC/gait controller — a concrete instance of the planning-over-control hierarchy for navigating unstructured terrain.

## Concepts
## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `DARPA_Caltech`
- DOI: https://doi.org/10.1109/TFR.2024.3512433
