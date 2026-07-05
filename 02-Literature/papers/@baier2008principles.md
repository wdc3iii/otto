---
type: paper
citekey: baier2008principles
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- C. Baier
- J. P. Katoen
year: 2008
venue: MIT Press
doi: null
arxiv: null
url: null
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- ModelChecking
---

# Principles of Model Checking

> [!info] C. Baier; J. P. Katoen · 2008 · MIT Press

## Summary
> [!note] AI-drafted from the book's established scope (no abstract; textbook) — verify against the source before citing specifics.
**TL;DR** — The standard graduate textbook on *model checking*: the theory and algorithms for automatically verifying whether a finite-state model of a system satisfies a formal temporal-logic specification.
**Problem** — A comprehensive, teachable treatment of formal verification — from system models through temporal logics to the underlying automata-theoretic algorithms — collected in one rigorous reference.
**Method** — Builds up transition systems and their properties, linear-time properties and Linear Temporal Logic (LTL), branching-time logics (CTL, CTL*), automata over infinite words (Büchi automata) for the automata-based approach to LTL model checking, equivalences and abstractions (bisimulation/simulation), and extensions to timed and probabilistic systems (including the state-explosion problem and symbolic techniques).
**Key results** — A unified, algorithmic account of specification (temporal logics) and verification (automata-theoretic and CTL model-checking algorithms), with correctness and complexity treated throughout.

## Takeaways
- The core dichotomy: linear-time (LTL, ω-automata) vs. branching-time (CTL/CTL*) specification, each with its own verification algorithm.
- State explosion is the central obstacle; abstraction, bisimulation quotients, and symbolic methods are the standard mitigations.
- Reference text for the formal-methods vocabulary (safety, liveness, fairness, refinement) that contract-based design borrows.

## Relevance to your work
Supplies the formal-methods foundations — temporal logic, safety/liveness, refinement — that assume-guarantee and contract-based control frameworks such as [[@contract2025theory]] rest on when they formalize and verify system-level specifications.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@contract2025theory]]
- bibkeys: `ModelChecking`
