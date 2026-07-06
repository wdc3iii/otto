---
type: paper
citekey: alan2023barrier
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- A. Alan
- A. J. Taylor
- C. R. He
- A. D. Ames
- G. Orosz
year: 2023
venue: TCST
doi: 10.1109/TCST.2023.3286090
arxiv: '2206.03568'
url: https://doi.org/10.1109/TCST.2023.3286090
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@alan2023barrier.pdf
bibkeys:
- AnilTCST23
---

# Control Barrier Functions and Input-to-State Safety with Application to Automated Vehicles

> [!info] A. Alan; A. J. Taylor; C. R. He; A. D. Ames; G. Orosz · 2023 · TCST
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A tutorial, constructive methodology for safety-critical control via control barrier functions (CBFs), extended to robust safety under disturbances through input-to-state safety (ISSf), demonstrated on a class-8 truck.
**Problem** — Balancing safety and performance without inducing unnecessary conservativeness, and doing so *robustly* when disturbances (e.g. unmodeled actuation dynamics) threaten the nominal safety guarantees.
**Method** — A hand-designed performance controller is filtered through a CBF to retain performant behavior while providing rigorous safety guarantees; robustness to disturbances is achieved via input-to-state safety (ISSf). The CBF design methodology is developed in parallel with an inverted-pendulum running example to make the design choices and sensitivities concrete, then applied to a connected automated vehicle.
**Key results** — Experimental deployment on a class-8 truck (no trailer) shows the impact of unmodeled actuation-system disturbances on CBF safety guarantees, which the ISSf framework characterizes and mitigates.

## Takeaways
- CBF-as-safety-filter: wrap a nominal/hand-designed controller and minimally modify it only to preserve set invariance.
- ISSf extends CBF safety to bounded disturbances, quantifying how much the safe set may shrink — the key robustness tool when actuation is imperfect.
- Tutorial framing (inverted-pendulum walkthrough) plus a real class-8-truck experiment makes design sensitivities concrete.

## Relevance to your work
A robust-safety CBF reference (input-to-state safety filtering under disturbances) directly relevant to safety-critical control synthesis; a companion to the CBF foundations behind [[@cohen2025safety]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@cohen2025safety]]
- bibkeys: `AnilTCST23`
