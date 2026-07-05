---
type: paper
citekey: glotfelter2017nonsmooth
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Glotfelter, Paul
- Cort\'es, Jorge
- Egerstedt, Magnus
year: 2017
venue: IEEE control systems letters
doi: 10.1109/LCSYS.2017.2710943
arxiv: null
url: https://doi.org/10.1109/LCSYS.2017.2710943
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- glotfelter2017nonsmooth
---

# Nonsmooth barrier functions with applications to multi-robot systems

> [!info] Glotfelter, Paul; Cort\'es, Jorge; Egerstedt, Magnus · 2017 · IEEE control systems letters

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Extends control barrier function theory to a class of *nonsmooth* barrier functions, enabling Boolean (max/min) compositions of multiple constraints for systems described by differential inclusions.
**Problem** — Satisfying multiple system-level constraints usually requires multiple barrier functions; combining them as Boolean logic formulas would be far more convenient but requires max/min operators that produce nonsmooth functions.
**Method** — The letter develops barrier-function guarantees for nonsmooth functions built from max and min operators over differential inclusions, extending previously established (smooth) barrier-function concepts to this setting so that constraints can be composed via Boolean formulas.
**Key results** — Validated by deploying Boolean compositions of nonsmooth barrier functions on a team of mobile robots.

## Takeaways
- Max/min composition lets many constraints collapse into a single (nonsmooth) barrier — a scalable way to encode Boolean constraint logic.
- Requires the differential-inclusion / nonsmooth-analysis machinery to recover forward-invariance guarantees.
- Demonstrated on multi-robot hardware, but the composition machinery is general to any CBF-constrained system.

## Relevance to your work
Nonsmooth/Boolean CBF composition is the tool for encoding multiple simultaneous safety constraints, directly relevant to safety-filter design as in [[@cohen2025safety]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025learning]]
- bibkeys: `glotfelter2017nonsmooth`
