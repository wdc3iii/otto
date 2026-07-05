---
type: paper
citekey: mazojr2024contract
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Mazo Jr, Manuel
- Compton, Will
- Cohen, Max H.
- Ames, Aaron D.
year: 2024
venue: arXiv:2409.14902 [eess]
doi: 10.48550/arXiv.2409.14902
arxiv: '2409.14902'
url: http://arxiv.org/abs/2409.14902
summary: ai-draft
pdf: attachments/@mazojr2024contract.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- mazo2024contract
---

# A Contract Theory for Layered Control Architectures

> [!info] Mazo Jr, Manuel; Compton, Will; Cohen, Max H.; Ames, Aaron D. · 2024 · arXiv:2409.14902 [eess]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A contract theory that formalizes layered (hierarchical) control architectures as relations between layers, so that composing per-layer contracts yields a contract for the whole system-wide specification.

**Problem** — Autonomous systems use layered control stacks mixing discrete and continuous models at different timescales, forming a new class of hybrid systems over heterogeneous signals; there is no principled way to design/analyze each layer in isolation while guaranteeing system-wide behavior.

**Method** — Formalizes a layered control architecture through a theory of relations between its layers. This enables contracts that define interfaces between layers and isolate each layer's design, with the guarantee that composition of the per-layer contracts produces a contract capturing the desired system-wide specification.

**Key results** — Yields a compositional methodology for analyzing layered control architectures; the contribution is the theoretical framework (relations, interfaces, compositional guarantee) rather than empirical benchmarks.

## Takeaways
- Treats a layered/hierarchical controller as a hybrid system over mixed discrete/continuous signals and multiple timescales, then tames it with contracts at layer interfaces.
- The central promise is compositionality: system-wide correctness follows from composing layer-local contracts, decoupling layer design.
- Provides the interface abstraction between, e.g., planning and continuous control layers.

## Relevance to your work
Directly foundational to a contract-based view of layered locomotion/navigation stacks — formalizing the interfaces that let planning, reduced-order, and full-order control layers be designed and verified separately ([[@contract2025theory]]).

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@contract2025theory]]
- bibkeys: `mazo2024contract`
- arXiv: https://arxiv.org/abs/2409.14902
- DOI: https://doi.org/10.48550/arXiv.2409.14902
- URL: http://arxiv.org/abs/2409.14902
