---
type: paper
citekey: girard2009hierarchical
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Antoine Girard
- George J. Pappas
year: 2009
venue: Automatica
doi: 10.1016/J.AUTOMATICA.2008.09.016
arxiv: null
url: https://doi.org/10.1016/j.automatica.2008.09.016
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- Girard2009
- GirardAutomatica09
---

# Hierarchical control system design using approximate simulation

> [!info] Antoine Girard; George J. Pappas · 2009 · Automatica

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces simulation functions (a quantitative version of simulation relations) that certify an output-error bound between a complex system and a simpler abstraction, enabling hierarchical control: design on the abstraction, then lift to the full system through an interface.
**Problem** — Formal-methods simulation relations are qualitative; there was no constructive, quantitative way to use a simplified abstraction to control a complex continuous system with a guaranteed error bound.
**Method** — Define a simulation function whose existence bounds the output distance between concrete system and abstraction. Control the abstraction, then lift the abstract control law to the concrete system via an interface. For linear control systems, give an effective characterization of simulation functions and interfaces amenable to algorithmic computation, plus guidance on choosing the abstraction.
**Key results** — Establishes the linear-systems theory and computation of simulation functions/interfaces; foundational rather than experimental.

## Takeaways
- Simulation functions are the quantitative certificate that makes abstract-then-lift hierarchical control rigorous — the output error stays within a computed bound.
- The abstraction/interface pattern (design low, execute high) is the conceptual template many later reduced-order + tracking-bound schemes reuse.
- The clean, computable theory is developed for linear systems; disturbances are not the focus (later work by Kurtz et al. adds robustness).

## Abstract (from bib)
In this paper, we present a new approach for hierarchical control based on the recent notions of approximate simulation and simulation functions, a quantitative version of the simulation relations. Given a complex system that needs to be controlled and a simpler abstraction, we show how the knowledge of a simulation function allows us to synthesize hierarchical control laws by first controlling the abstraction and then lifting the abstract control law to the complex system using an interface. For the class of linear control systems, we give an effective characterization of the simulation functions and of the associated interfaces. This characterization allows us to use algorithmic procedures for their computation. We show how to choose an abstraction for a linear control system such that o

## Relevance to your work
The origin of simulation-function-based hierarchical control and the abstraction/interface + output-error-bound pattern that grounds reduced-order planning with a certified tracking bound in [[@compton2025dynamic]].

## Concepts
[[reduced-order-model]] [[hierarchical-control]] [[tracking-error-bound]]

## Source
- Cited by [[@cohen2025safety]], [[@compton2025dynamic]]
- bibkeys: `Girard2009`, `GirardAutomatica09`
- DOI: https://doi.org/10.1016/J.AUTOMATICA.2008.09.016
