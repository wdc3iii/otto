---
type: paper
citekey: tabuada2009verification
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Tabuada, Paulo
year: 2009
venue: Springer Science \& Business Media
doi: 10.1007/978-1-4419-0224-5
arxiv: null
url: https://doi.org/10.1007/978-1-4419-0224-5
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- Paulo
- Tabuada
- tabuada2009verification
---

# Verification and control of hybrid systems: a symbolic approach

> [!info] Tabuada, Paulo · 2009 · Springer Science \& Business Media

## Summary
> [!note] AI-drafted from the book's scope (abstract unavailable) — a base to refine.
**TL;DR** — A monograph presenting a unified symbolic approach to the verification and controller synthesis of continuous and hybrid systems by constructing finite-state abstractions.
**Problem** — Continuous and hybrid dynamics have infinite state spaces, so algorithmic (automata-theoretic) verification and correct-by-construction control synthesis cannot be applied directly.
**Method** — The book develops system relations — (bi)simulation and approximate/alternating (bi)simulation relations — that let a continuous system be abstracted by a finite symbolic model preserving the properties of interest, so specifications (e.g. temporal-logic) can be checked and controllers synthesized on the finite abstraction and refined back to the concrete system.
**Key results** — A self-contained theory connecting incremental stability, approximate bisimulation, and the existence of finite symbolic abstractions for controller synthesis.

## Takeaways
- Central idea: approximate (bi)simulation relations formalize when a simpler/finite model faithfully stands in for a complex one — a rigorous notion of a "correct" abstraction.
- Enables correct-by-construction synthesis against rich (temporal-logic) specifications, at the cost of building and refining finite abstractions.
- A theoretical reference text, not an empirical result.

## Relevance to your work
The (approximate) simulation/abstraction relations formalized here are the mathematical machinery behind layered and contract-based control design — they ground the abstraction relations used in [[@contract2025theory]].

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@cohen2025safety]], [[@contract2025theory]], [[@hierarchies2025motion]]
- bibkeys: `Paulo`, `Tabuada`, `tabuada2009verification`
