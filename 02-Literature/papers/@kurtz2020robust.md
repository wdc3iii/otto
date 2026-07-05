---
type: paper
citekey: kurtz2020robust
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Vince Kurtz
- Patrick M. Wensing
- Hai Lin
year: 2020
venue: Proceedings of the American Control Conference
doi: 10.23919/ACC45564.2020.9147511
arxiv: 2003.04136
url: https://arxiv.org/abs/2003.04136
zotero: null
summary: ai-draft
pdf: attachments/@kurtz2020robust.pdf
status: to-read
mine: false
bibkeys:
- Kurtz2020
---

# Robust Approximate Simulation for Hierarchical Control of Linear Systems under Disturbances

> [!info] Vince Kurtz; Patrick M. Wensing; Hai Lin · 2020 · Proceedings of the American Control Conference

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Extends approximate simulation to disturbed systems: a "robust approximate simulation" relation yields output-error bounds between a concrete system and its abstraction even under external disturbances, for linear systems with either bounded or impulse disturbances.
**Problem** — Standard approximate simulation (à la Girard-Pappas) certifies an abstraction-to-concrete output-error bound but ignores external disturbances, so its guarantees don't hold for real disturbed systems.
**Method** — Define robust approximate simulation accounting for disturbances on the concrete system, and derive output-error bounds for linear systems under two disturbance models: bounded additive disturbances and a sequence of (unbounded) impulse disturbances. Illustrate the need for and effectiveness of the approach on a simulated robot motion-planning example.
**Key results** — Provides closed-form-style output-error bounds under both disturbance types; demonstrated on a simulated robot motion-planning task.

## Takeaways
- Adds disturbance robustness to the Girard-Pappas simulation-function framework — the abstraction's error bound now holds despite external perturbations.
- Treats two disturbance regimes (bounded and impulse) separately, both for linear systems.
- The certified output-error bound is exactly the tube margin a higher layer needs to plan safely under disturbance.

## Abstract (from bib)
Approximate simulation, an extension of simulation relations from formal methods to continuous systems, is a powerful tool for hierarchical control of complex systems. Finding an approximate simulation relation between the full "concrete" system and a simplified "abstract" system establishes a bound on the output error between the two systems, allowing one to design a controller for the abstract system while formally certifying performance on the concrete system. However, many real-world control systems are subject to external disturbances, which are not accounted for in the standard approximate simulation framework. We present a notion of robust approximate simulation, which considers external disturbances to the concrete system. We derive output error bounds for the case of linear system

## Relevance to your work
The disturbance-robust version of approximate-simulation hierarchical control — its certified output-error bound under disturbances is conceptually the tracking tube that [[@compton2025dynamic]] makes dynamic and learns rather than fixes offline.

## Concepts
[[reduced-order-model]] [[hierarchical-control]] [[tracking-error-bound]]

## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `Kurtz2020`
- DOI: https://doi.org/10.23919/ACC45564.2020.9147511
