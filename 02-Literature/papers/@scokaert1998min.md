---
type: paper
citekey: scokaert1998min
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Scokaert, Pierre OM
- Mayne, David Q
year: 1998
venue: IEEE Transactions on Automatic control
doi: 10.1109/9.704989
arxiv: null
url: https://doi.org/10.1109/9.704989
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- scokaert1998min
---

# Min-max feedback model predictive control for constrained linear systems

> [!info] Scokaert, Pierre OM; Mayne, David Q · 1998 · IEEE Transactions on Automatic control

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Formulates min-max feedback model predictive control for constrained linear systems, where the receding-horizon optimization plans over feedback policies rather than open-loop input sequences.
**Problem** — Standard (open-loop) min-max MPC against bounded disturbances is conservative and prone to feasibility loss, because a single input sequence must be robust to every disturbance realization.
**Method** — The authors introduce the notion that feedback is present in the receding-horizon implementation, optimizing over control policies (in both fixed- and variable-horizon settings) so the predicted control can react to disturbances; they analyze stability and discuss practical implementation.
**Key results** — Shows improved performance over standard MPC and resolves the feasibility difficulties documented for prior min-max techniques, with stabilizing guarantees.

## Takeaways
- The key conceptual move — optimizing over feedback policies instead of open-loop inputs — is the ancestor of modern tube and constraint-tightening robust MPC.
- Reduces the conservatism/infeasibility of open-loop min-max MPC, at the cost of a harder optimization over policies.
- Restricted to constrained linear systems with bounded disturbances.

## Relevance to your work
Foundational robust-MPC reference: the feedback-policy view of receding-horizon control underlies the constraint-tightening and tube constructions used in robust layered planning like [[@csomayshanklin2024robust]].

## Concepts
[[tube-mpc]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `scokaert1998min`
