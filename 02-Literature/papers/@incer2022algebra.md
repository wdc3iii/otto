---
type: paper
citekey: incer2022algebra
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Incer, I
year: 2022
venue: 'PhD thesis, EECS, UC Berkeley (Tech. Rep. EECS-2022-99)'
doi: null
arxiv: null
url: https://www2.eecs.berkeley.edu/Pubs/TechRpts/2022/EECS-2022-99.html
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@incer2022algebra.pdf
bibkeys:
- Incer
---

# The algebra of contracts

> [!info] Incer, I · 2022 · —

## Summary
> [!note] AI-drafted from the thesis abstract / EECS tech-report description — a base to refine.
**TL;DR** — A PhD thesis that builds a general algebra for assume-guarantee (AG) contracts and generalizes it to *hypercontracts*, giving compositional operators for specifying and reasoning about components as pairs of assumptions and guarantees.
**Problem** — Contract-based design lets engineers reason about systems component-by-component, but the existing AG theory was tied to trace/behavioral properties and lacked a unified algebraic treatment covering the full set of operations designers need (composition, refinement, and inverses like quotient/merging).
**Method** — Incer develops the algebraic structure underlying contracts — the lattice/order of specifications and the operators on it — and introduces hypercontracts, an AG theory where assumptions and guarantees are arbitrary *hyperproperties* rather than plain properties. This extends AG reasoning to attributes (security, information-flow, ML-style properties) that cannot be expressed as trace properties.
**Key results** — Provides a coherent set of contract operations (composition, quotient/residuation, merging, refinement) with their algebraic laws, and shows the hypercontract framework subsumes prior contract theories as special cases.

## Takeaways
- Positions contracts as an *algebra*: composition and its inverses (quotient, separation) are the load-bearing operators for compositional system design.
- Hypercontracts widen AG reasoning from trace properties to hyperproperties, so the same machinery covers safety, security, and learning-style specs.
- Foundational/theoretical (formal methods lineage: Sangiovanni-Vincentelli, Passerone, Nuzzo); it is the reference for the algebra, not for a specific control application.

## Relevance to your work
This is the algebraic backbone behind contract-based approaches to layered/networked control; it grounds the operator laws (composition, refinement, quotient) that a control-contracts framework like [[@contract2025theory]] leans on when it argues about composing guarantees across a control stack.

## Concepts


## Source
- Cited by [[@contract2025theory]]
- bibkeys: `Incer`
