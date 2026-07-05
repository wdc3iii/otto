---
type: paper
citekey: belta2017formal
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- C. Belta
- B. Yordanov
- E. A. Gol
year: 2017
venue: Springer
doi: 10.1007/978-3-319-50763-7
arxiv: null
url: https://doi.org/10.1007/978-3-319-50763-7
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- Belta
- Calin
---

# Formal Methods for Discrete-Time Dynamical Systems

> [!info] C. Belta; B. Yordanov; E. A. Gol · 2017 · Springer

## Summary
> [!note] AI-drafted from the abstract — a base to refine.

**TL;DR** — A self-contained textbook that bridges control theory and formal methods, showing how to analyze and control discrete-time dynamical systems against temporal-logic specifications via finite abstractions.

**Problem** — Control theory and formal methods developed largely separately; there was no accessible, unified treatment for synthesizing controllers that provably satisfy rich (temporal-logic) specifications on dynamical systems.

**Method** — Rigorously defines the formal-methods machinery (transition systems, temporal logics, model checking, synthesis) and links it to infinite-state dynamical systems through intuitive abstractions requiring only basic convex-analysis and control terminology (supplied in an appendix). Focuses on discrete-time linear and piecewise-affine systems while giving general frameworks for abstraction, analysis, and control.

**Key results** — A pedagogical, self-contained framework connecting model checking / temporal-logic synthesis to control of discrete-time systems; not an empirical results paper.

## Takeaways
- The standard entry-point reference tying temporal logic and model checking to control synthesis.
- Finite abstractions of (piecewise-)affine dynamics are the bridge that makes formal verification/synthesis tractable.
- Assumes little formal-methods or control background — useful as a teaching text.

## Relevance to your work
Grounds the formal-methods / temporal-logic vocabulary behind safety and contract-based control frameworks such as [[@contract2025theory]] and safety-critical control work.

## Concepts



## Source
- Cited by [[@cohen2025safety]], [[@contract2025theory]]
- bibkeys: `Belta`, `Calin`
