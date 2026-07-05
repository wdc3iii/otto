---
type: paper
citekey: saoud2021assume
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Adnane Saoud
- Antoine Girard
- Laurent Fribourg
year: 2021
venue: Automatica
doi: 10.1016/j.automatica.2021.109910
arxiv: null
url: https://doi.org/10.1016/j.automatica.2021.109910
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@saoud2021assume.pdf
bibkeys:
- Saoud
---

# Assume-guarantee contracts for continuous-time systems

> [!info] Adnane Saoud; Antoine Girard; Laurent Fribourg · 2021 · Automatica

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Develops assume-guarantee (AG) contracts and compositional reasoning to verify invariance properties of interconnected discrete- and continuous-time dynamical systems, so a global guarantee follows from each component satisfying its own contract.
**Problem** — Verifying properties (notably invariance/safety) of large interconnected dynamical systems monolithically is hard; a compositional contract theory tailored to continuous-time dynamics (and their interconnections, including feedback cycles) was needed.
**Method** — The paper defines *weak* and *strong* satisfaction semantics for AG contracts and proves compositional results: satisfying all component contracts implies the system-level contract. Weak satisfaction suffices when the interconnection is a directed acyclic graph; strong satisfaction is required for general (cyclic/feedback) interconnections. For systems given as differential inclusions with invariance-type contracts, weak satisfaction is shown to suffice even for general interconnections. The invariance contracts build on the classical characterization of invariant sets for differential inclusions.
**Key results** — A unified weak/strong AG-contract framework spanning discrete- and continuous-time systems, with cycle-vs-DAG conditions for sound compositional invariance verification.

## Takeaways
- The weak/strong distinction is the crux: acyclic interconnections are easy (weak), cycles need the stronger notion — except invariance-on-differential-inclusions, which stays weak.
- Grounds compositional safety/invariance in classical invariant-set theory for differential inclusions, connecting formal-methods contracts to control-theoretic set invariance.
- Continuous-time and interconnection-aware, unlike much earlier discrete/hybrid AG work.

## Relevance to your work
Directly relevant to safety-by-contract for control: it supplies the continuous-time, invariance-flavored AG semantics that a control-contracts framework like [[@contract2025theory]] can build on to compose safety guarantees (e.g., forward-invariant safe sets) across interconnected subsystems.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@contract2025theory]]
- bibkeys: `Saoud`
