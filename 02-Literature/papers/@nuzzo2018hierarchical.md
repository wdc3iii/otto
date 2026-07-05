---
type: paper
citekey: nuzzo2018hierarchical
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Nuzzo, Pierluigi
- Sangiovanni-Vincentelli, Alberto L
year: 2018
venue: 'Principles of Modeling: Essays Dedicated to E. A. Lee on the Occasion of His
  60th Birthday'
doi: 10.1007/978-3-319-95246-8_22
arxiv: null
url: https://doi.org/10.1007/978-3-319-95246-8_22
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- Nuzzo
---

# Hierarchical system design with vertical contracts

> [!info] Nuzzo, Pierluigi; Sangiovanni-Vincentelli, Alberto L · 2018 · Principles of Modeling: Essays Dedicated to E. A. Lee on the Occasion of His 60th Birthday

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces *heterogeneous refinement* and *vertical contracts* as additions to any contract framework, giving methodological support for multi-view, multi-layer system design that mixes heterogeneous models and formalisms across levels of abstraction.
**Problem** — Standard contract refinement relates specifications within a single homogeneous formalism; layered ("vertical") design spans architectures and behaviors expressed in different formalisms, which classical horizontal refinement doesn't capture.
**Method** — The paper rethinks the refinement relation for layered design and extends it via heterogeneous refinement (relating models across formalisms) and vertical contracts, which state the conditions under which an aggregation of lower-level components satisfies the requirements posed at a higher level of abstraction. Design examples illustrate the richer set of refinement relations, including support for synthesis and optimized mapping of specifications to implementations.
**Key results** — A framework-agnostic extension enabling contract-based reasoning across a hierarchy of heterogeneous models, connecting high-level specs to implementations through vertical contracts.

## Takeaways
- "Vertical" contracts formalize cross-layer obligations (what lower layers must guarantee for an upper-layer spec to hold) — distinct from "horizontal" composition of peers.
- Framework-agnostic: intended as an add-on to existing contract theories rather than a new standalone one.
- Essay-style chapter (Festschrift for Edward A. Lee); conceptual/methodological rather than a specific verified control system.

## Relevance to your work
Vertical/heterogeneous refinement is the abstraction that lets a layered control stack — high-level planner over mid-level template over low-level policy — be tied together by contracts; a control-contracts theory like [[@contract2025theory]] uses exactly this cross-layer obligation structure.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@contract2025theory]]
- bibkeys: `Nuzzo`
