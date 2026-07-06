---
type: paper
citekey: rosolia2022unified
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Rosolia, Ugo
- Singletary, Andrew
- Ames, Aaron D.
year: 2022
venue: IEEE Transactions on Automatic Control
doi: 10.1109/TAC.2022.3184664
arxiv: '2012.06558'
url: https://doi.org/10.1109/TAC.2022.3184664
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@rosolia2022unified.pdf
bibkeys:
- Ames-Multirate
- rosolia_unified_2022
---

# Unified multirate control: From low-level actuation to high-level planning

> [!info] Rosolia, Ugo; Singletary, Andrew; Ames, Aaron D. · 2022 · IEEE Transactions on Automatic Control
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A three-layer multirate control architecture — a high-level MOMDP policy, a mid-level MPC planner, and a low-level CBF tracking controller — that satisfies temporal-logic specifications in partially observed environments while guaranteeing state/input constraints.
**Problem** — Nonlinear autonomous systems must satisfy high-level (temporal-logic) objectives under partial observability while respecting hard state and input constraints, spanning very different timescales.
**Method** — Objectives are expressed as syntactically co-safe LTL. The system-environment interaction is modeled as a discrete Mixed Observable MDP (MOMDP); the high-level policy updates the constraint sets and cost of an MPC that plans a reference trajectory; a low-level high-frequency controller uses Control Barrier Functions to guarantee bounded tracking error. Layers use model abstractions of increasing complexity and run at different frequencies.
**Key results** — The architecture provably maximizes the probability of satisfying the high-level spec while guaranteeing constraint satisfaction; validated in simulation and experiments on Mars-exploration-inspired tasks with partial observations.

## Takeaways
- A concrete instantiation of layered control: discrete planning / MPC / continuous tracking, each at its own rate and abstraction level.
- CBF-based tracking bounds are the interface guarantee that lets the higher layers reason on a simpler model.
- Handles partial observability explicitly via the MOMDP, not just deterministic planning.

## Relevance to your work
A canonical multirate/layered control template with certified inter-layer tracking guarantees; cited by [[@contract2025theory]] as prior art for the contract-style interfaces between planning and tracking layers.

## Concepts
[[hierarchical-control]], [[control-barrier-function]], [[tracking-error-bound]]

## Source
- Cited by [[@contract2025theory]], [[@hierarchies2025motion]]
- bibkeys: `Ames-Multirate`, `rosolia_unified_2022`
