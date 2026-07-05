---
type: paper
citekey: dixit2024step
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Dixit, Anushri
- Fan, David D
- Otsu, Kyohei
- Dey, Sharmita
- Agha-Mohammadi, Ali-Akbar
- Burdick, Joel
year: 2024
venue: Field Robotics
doi: null
arxiv: 2303.01614
url: https://arxiv.org/abs/2303.01614
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@dixit2024step.pdf
bibkeys:
- dixit2024step
---

# Step: Stochastic traversability evaluation and planning for risk-aware navigation; results from the darpa subterranean challenge

> [!info] Dixit, Anushri; Fan, David D; Otsu, Kyohei; Dey, Sharmita; Agha-Mohammadi, Ali-Akbar; Burdick, Joel · 2024 · Field Robotics

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A risk-aware perception-and-planning stack (STEP) that lets ground robots traverse unknown, perceptually-degraded subterranean terrain by explicitly reasoning about the tail risk of traversability estimates.
**Problem** — Autonomous off-road/underground navigation must act on uncertain, incomplete terrain estimates where a single mis-assessed patch can immobilize the robot; deterministic traversability costs ignore this risk.
**Method** — Five coupled components: (1) rapid uncertainty-aware mapping and traversability evaluation, (2) tail-risk assessment via Conditional Value-at-Risk (CVaR), (3) risk- and constraint-aware kinodynamic motion planning using SQP-based MPC, (4) fast recovery behaviors for failure cases, and (5) risk-based gait adaptation for quadrupeds.
**Key results** — Validated on wheeled and legged platforms in field trials (Valentine Cave CA, Kentucky Underground mine, Louisville Mega Cavern) as part of the DARPA Subterranean Challenge.

## Takeaways
- CVaR gives a principled knob to trade off aggressiveness vs. safety under traversability uncertainty, rather than tuning heuristic cost inflation.
- The system is a full deployed autonomy stack (mapping → risk → MPC planning → recovery), so its value is systems-integration and field robustness more than a single algorithmic novelty.
- Legged-robot support is via gait adaptation layered on top of a wheeled-oriented planner, not a whole-body locomotion controller.

## Relevance to your work
A reference point for risk-aware terrain traversability and MPC-based navigation planning on legged/ground robots — directly relevant to the navigation-autonomy layer above a locomotion controller in [[@terrain2026consistent]].

## Concepts


## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `dixit2024step`
