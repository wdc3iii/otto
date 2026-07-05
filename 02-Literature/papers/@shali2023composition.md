---
type: paper
citekey: shali2023composition
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Shali, Brayan M.
- van der Schaft, Arjan
- Besselink, Bart
year: 2023
venue: IEEE Transactions on Automatic Control
doi: 10.1109/TAC.2022.3233290
arxiv: null
url: https://research.rug.nl/en/publications/d4efb264-15d1-4b2c-b355-8ae4d0750903
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- Shali
---

# Composition of Behavioural Assume–Guarantee Contracts

> [!info] Shali, Brayan M.; van der Schaft, Arjan; Besselink, Bart · 2023 · IEEE Transactions on Automatic Control

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Formalizes assume–guarantee contracts for continuous linear dynamical systems using the behavioral approach, with composition rules for both series and feedback interconnections.

**Problem** — Contract-based design has succeeded for discrete software systems but is largely absent for continuous dynamical systems; complex engineering systems need an inherently modular design/analysis method.

**Method** — Contracts specify a system through *assumptions* (dynamic behavior of the environment supplying inputs) and *guarantees* (desired output behavior when interconnected with a valid environment), formalized via Willems' behavioral systems theory. The paper defines and characterizes contract implementation, contract refinement (to compare contracts), and two notions of composition covering series and feedback interconnections.

**Key results** — Establishes that refinement and composition properties let contracts be used for modular design and analysis of linear I/O systems; provides characterizations rather than reported numerical experiments.

## Takeaways
- Brings assume–guarantee reasoning into continuous LTI systems via the behavioral framework, not just discrete/software abstractions.
- Two composition notions (series and feedback) are the key enabler for reasoning about interconnected continuous systems compositionally.
- Scope is linear dynamical systems with inputs/outputs — a limitation for nonlinear or hybrid control stacks.

## Relevance to your work
Provides the behavioral-systems foundation for assume–guarantee contracts between dynamical subsystems, directly informing compositional guarantees in a layered control stack ([[@contract2025theory]]).

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@contract2025theory]]
- bibkeys: `Shali`
- DOI: https://doi.org/10.1109/TAC.2022.3233290
