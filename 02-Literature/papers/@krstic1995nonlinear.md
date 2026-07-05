---
type: paper
citekey: krstic1995nonlinear
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- M. Krstic
- I. Kanellakopoulos
year: 1995
venue: Wiley
doi: null
arxiv: null
url: null
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- Krstic
---

# Nonlinear and Adaptive Control Design

> [!info] M. Krstic; I. Kanellakopoulos · 1995 · Wiley

## Summary
> [!note] AI-drafted from the book's established scope (no abstract; textbook) — verify against the source before citing specifics.
**TL;DR** — The foundational monograph on *backstepping*: a systematic, recursive Lyapunov-based methodology for the design of stabilizing and adaptive controllers for nonlinear systems.
**Problem** — Prior nonlinear/adaptive control lacked a constructive, general procedure; feedback-linearization-style methods cancelled useful nonlinearities and adaptive schemes suffered from overparametrization.
**Method** — Develops integrator backstepping — building a control Lyapunov function and control law recursively through cascade/strict-feedback structure — and extends it to adaptive backstepping with the *tuning-functions* design that avoids overparametrization, plus modular designs separating the identifier from the controller.
**Key results** — Provides constructive stability/tracking guarantees for broad classes of nonlinear systems (strict-feedback, parametric-strict-feedback) and became the standard reference establishing backstepping and adaptive backstepping.

## Takeaways
- Backstepping is a Lyapunov-*constructive* method: the CLF and controller are built together, recursively, rather than assumed.
- Tuning functions solve the overparametrization problem in adaptive backstepping — a key practical contribution.
- Assumes structured (strict-feedback) dynamics and known structure; the recursion's complexity grows with system order.

## Relevance to your work
Backstepping and its Lyapunov-constructive philosophy underpin much CLF-based and safety-critical nonlinear control; it is the classical lineage that adaptive/robust safe-control work such as [[@cohen2025safety]] extends toward CBF/robustness guarantees.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@cohen2025safety]], [[@contract2025theory]]
- bibkeys: `Krstic`
