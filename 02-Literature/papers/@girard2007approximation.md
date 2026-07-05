---
type: paper
citekey: girard2007approximation
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- A. Girard
- G. J. Pappas
year: 2007
venue: IEEE Transactions on Automatic Control
doi: 10.1109/TAC.2007.895849
arxiv: null
url: https://doi.org/10.1109/TAC.2007.895849
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- Girard
---

# Approximation Metrics for Discrete and Continuous Systems

> [!info] A. Girard; G. J. Pappas · 2007 · IEEE Transactions on Automatic Control

## Summary
> [!note] AI-drafted from the abstract — a base to refine.

**TL;DR** — Introduces approximate versions of language inclusion, simulation, and bisimulation, together with a hierarchy of pseudo-metrics that quantify how well one system approximates another, applicable uniformly to discrete and continuous systems.

**Problem** — Classical exact notions of language inclusion and (bi)simulation are too rigid for continuous and hybrid systems, where one wants to say two systems are *close* rather than exactly equivalent, with a quantitative bound.

**Method** — Develops the first framework of system approximation covering both discrete and continuous systems by defining approximate language inclusion, approximate simulation, and approximate bisimulation relations. Defines a hierarchy of approximation pseudo-metrics between two systems that quantify approximation quality, and proves the framework is compositional under a synchronous composition operator.

**Key results** — A unified, quantitative theory of system approximation with compositionality guarantees under synchronous composition (a foundational-theory contribution rather than an empirical one).

## Takeaways
- Approximate (bi)simulation with metric bounds is the tool that makes finite abstraction of continuous systems rigorous — you get a quantified error, not just yes/no equivalence.
- Compositionality under synchronous composition is what lets these metrics be used in modular verification.
- A cornerstone reference for abstraction-based control and formal analysis of hybrid systems.

## Relevance to your work
Provides the quantitative approximate-simulation metrics underlying reduced-order / abstraction-based control and error-bounded layered design, connecting to [[@contract2025theory]].

## Concepts
[[reduced-order-model]] [[tracking-error-bound]]

## Source
- Cited by [[@contract2025theory]]
- bibkeys: `Girard`
