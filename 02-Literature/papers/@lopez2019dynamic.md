---
type: paper
citekey: lopez2019dynamic
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Lopez, Brett T
- Slotine, Jean-Jacques E
- How, Jonathan P
year: 2019
venue: 2019 American Control Conference (ACC)
doi: null
arxiv: '1907.06553'
url: https://arxiv.org/abs/1907.06553
summary: ai-draft
pdf: attachments/@lopez2019dynamic.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- Lopez2019
---

# Dynamic tube MPC for nonlinear systems

> [!info] Lopez, Brett T; Slotine, Jean-Jacques E; How, Jonathan P · 2019 · 2019 American Control Conference (ACC)

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Dynamic Tube MPC (DTMPC): a nonlinear-systems framework that optimizes the tube geometry *and* the nominal open-loop trajectory simultaneously, so the tube adapts online with little added computational cost.
**Problem** — Classical tube MPC fixes a robust controller/tube offline, which is suboptimal under changing objectives and can't capture state-dependent uncertainty; computing invariant tubes for nonlinear systems is expensive and yields overly conservative approximations.
**Method** — Use boundary-layer sliding control so the tube geometry becomes a simple algebraic relation between control parameters and the uncertainty bound. This lets the tube-geometry dynamics be appended to the nominal MPC optimization with minimal complexity increase, and lets DTMPC exploit state-dependent uncertainty to cut conservativeness and improve feasibility.
**Key results** — Demonstrated on robust obstacle avoidance, where the tube geometry contracts/expands in response to obstacle proximity.

## Takeaways
- Key trick: sliding-mode boundary-layer control gives a closed-form tube-size ↔ uncertainty-bound map, so the tube can be a decision variable in the MPC rather than a fixed offline object.
- State-dependent (rather than worst-case constant) uncertainty is what buys reduced conservativeness and feasibility.
- Directly the "dynamic tube" idea — the tube cross-section is time/state-varying and co-optimized with the plan.

## Relevance to your work
The direct antecedent of dynamic-tube planning for locomotion: [[@compton2025dynamic]] extends this co-optimization of tube geometry and nominal trajectory to the legged setting.

## Concepts
[[tube-mpc]] · [[dynamic-tube]] · [[tracking-error-bound]]

## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `Lopez2019`
