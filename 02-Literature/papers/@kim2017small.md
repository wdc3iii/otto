---
type: paper
citekey: kim2017small
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Kim, Eric S.
- Arcak, Murat
- Seshia, Sanjit A.
year: 2017
venue: 'Proceedings of the 20th International Conference on Hybrid Systems: Computation
  and Control'
doi: 10.1145/3049797.3049805
arxiv: null
url: https://doi.org/10.1145/3049797.3049805
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- Kim
---

# A Small Gain Theorem for Parametric Assume-Guarantee Contracts

> [!info] Kim, Eric S.; Arcak, Murat; Seshia, Sanjit A. · 2017 · Proceedings of the 20th International Conference on Hybrid Systems: Computation and Control

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces *parametric* assume-guarantee (AG) contracts and proves a generalized small-gain theorem for them, unifying formal-methods AG reasoning with control-theoretic input-output/small-gain analysis for verifying networked cyber-physical systems.
**Problem** — Verifying properties of large, networked CPS is intractable monolithically. Two divide-and-conquer traditions exist in isolation: AG contracts (formal methods) and input-output properties like finite gain (control theory).
**Method** — The paper defines a parametric AG contract that reasons about system behavior abstractly in a *parameter domain*, then encodes a finite-gain property in that form and derives a generalized small-gain theorem for the interconnection of parametric AG contracts. The classical small-gain theorem drops out as a special case, exposing the link between AG reasoning and small-gain results.
**Key results** — The new theorem extends beyond bounded deviation from a nominal point to a fragment of linear temporal logic with parametrized predicates, capturing safety, recurrence, and liveness. Validated on a freeway example certifying intermittent congestion of two interconnected segments.

## Takeaways
- Bridges two verification cultures: shows classical small-gain is a special case of compositional AG reasoning over a parameter domain.
- Parametric predicates let one contract framework express not just bounded-error (stability-style) properties but temporal-logic safety/recurrence/liveness.
- Compositional guarantee: a global contract holds if the components satisfy theirs — the scalability payoff for networked CPS.
- Demonstrated on a traffic-network example; the machinery is discrete/hybrid-flavored rather than tuned to continuous nonlinear dynamics.

## Relevance to your work
The small-gain-as-AG-contract view is exactly the kind of compositional certificate a control-contracts theory such as [[@contract2025theory]] builds on to reason about interconnected/layered controllers without monolithic verification.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@contract2025theory]]
- bibkeys: `Kim`
- DOI: https://doi.org/10.1145/3049797.3049805
- URL: https://doi.org/10.1145/3049797.3049805
