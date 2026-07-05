---
type: paper
citekey: pappas2000hierarchically
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- G. J. Pappas
- G. Lafferriere
- S. Sastry
year: 2000
venue: TAC
doi: 10.1109/9.863598
arxiv: null
url: https://doi.org/10.1109/9.863598
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- PappasTAC00
---

# Hierarchically Consistent Control Systems

> [!info] G. J. Pappas; G. Lafferriere; S. Sastry · 2000 · TAC

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Defines a notion of modeling hierarchy for continuous control systems and characterizes when a coarse, aggregated higher-level model is *hierarchically consistent* with the detailed lower-level model with respect to controllability.
**Problem** — Large-scale control systems are organized hierarchically, with higher levels using coarser (aggregated) models; a high-level plan is only useful if the lower level can actually implement it. Formalizing that guarantee — hierarchical consistency — was open for continuous control systems.
**Method** — The paper defines a modeling hierarchy for continuous control systems (higher-level models arise by aggregating lower-level ones) and derives characterizations of hierarchically consistent linear systems with respect to controllability objectives.
**Key results** — As a byproduct, it obtains a hierarchical controllability criterion for linear systems that recovers the best known controllability algorithms from numerical linear algebra.

## Takeaways
- Hierarchical consistency is the property that makes abstraction *safe*: solvability at the abstract level implies solvability at the detailed level.
- The results are established for linear systems and controllability objectives — a foundational but restricted setting later generalized (e.g., to affine systems).
- Aggregation/abstraction of models is cast as a formal map between systems, not an informal engineering simplification.

## Relevance to your work
This is the control-theoretic root of layered/hierarchical control: it formalizes when planning on a reduced abstract model is guaranteed to be realizable on the full system — the guarantee that modern layered locomotion and reduced-order safety schemes like [[@cohen2025safety]] depend on.

## Concepts
[[hierarchical-control]] · [[reduced-order-model]]

## Source
- Cited by [[@cohen2025safety]]
- bibkeys: `PappasTAC00`
