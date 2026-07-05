---
type: paper
citekey: benveniste2018contracts
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Benveniste, Albert
- others
year: 2018
venue: Foundations and Trends\textregistered in Electronic Design Automation
doi: 10.1561/1000000053
arxiv: null
url: https://doi.org/10.1561/1000000053
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- Benveniste
---

# Contracts for system design

> [!info] Benveniste, Albert; others · 2018 · Foundations and Trends\textregistered in Electronic Design Automation

## Summary
> [!note] AI-drafted from the abstract — a base to refine.

**TL;DR** — A comprehensive monograph that builds a unifying meta-theory of contracts for system design and uses it to compare existing contract frameworks (interface theories, assume-guarantee, etc.).

**Problem** — System-design complexity demands a rigorous, compositional way to specify what a component assumes of its environment and guarantees in return, but the many existing contract frameworks lacked a common foundation for comparison.

**Method** — Presents contract-based design as an approach orthogonal to and complementing existing methodologies, providing scaffolding for verification, analysis, abstraction/refinement, and synthesis. Develops a new mathematical meta-theory of contracts as the foundation, then instantiates it to explain and relate several concrete contract frameworks and assess their similarities and differences.

**Key results** — A self-contained treatment illustrated on two case studies: requirements engineering for a parking-garage management system, and timing/scheduling contracts within the AUTOSAR automotive methodology.

## Takeaways
- The canonical reference framing of assume-guarantee / contract-based design; establishes the meta-theory others specialize.
- Contracts support the full compositional workflow — refinement, abstraction, verification, and synthesis — not just specification.
- Framework-agnostic: its value is unifying and comparing prior contract theories rather than proposing one more.

## Relevance to your work
The foundational text for contract-based / assume-guarantee reasoning that underpins layered control-theory frameworks like [[@contract2025theory]].

## Concepts



## Source
- Cited by [[@contract2025theory]]
- bibkeys: `Benveniste`
