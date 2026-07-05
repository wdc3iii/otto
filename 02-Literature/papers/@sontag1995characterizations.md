---
type: paper
citekey: sontag1995characterizations
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Sontag, Eduardo D.
- Wang, Yuan
year: 1995
venue: Systems \& Control Letters
doi: 10.1016/0167-6911(94)00050-6
arxiv: null
url: https://www.sciencedirect.com/science/article/pii/0167691194000506
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- sontag_characterizations_1995
---

# On characterizations of the input-to-state stability property

> [!info] Sontag, Eduardo D.; Wang, Yuan · 1995 · Systems \& Control Letters

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Proves that the Lyapunov sufficient condition for input-to-state stability (ISS) is also necessary, giving several equivalent characterizations of the property.
**Problem** — ISS had a well-known Lyapunov sufficient condition, but whether it was necessary (i.e., whether ISS *implies* the existence of an ISS-Lyapunov function) was an open question raised by several authors.
**Method** — Establishes the equivalence between ISS and the existence of a smooth ISS-Lyapunov function, and derives additional equivalent characterizations, including one phrased in terms of nonlinear stability margins.
**Key results** — Settles the open question positively: the Lyapunov condition is necessary as well as sufficient, so ISS admits a dissipation-style Lyapunov characterization and can equivalently be described via nonlinear robustness/stability margins.

## Takeaways
- One of the foundational results making ISS a *checkable* property: ISS ⇔ existence of an ISS-Lyapunov function, not just ⇐.
- Provides multiple equivalent lenses on the same property (Lyapunov dissipation, stability margins), which is why the paper is a standard citation when justifying ISS-based arguments.
- Applies to general nonlinear systems with inputs; the equivalences are what later robustness analyses lean on.

## Abstract (from bib)
We show that the well-known Lyapunov sufficient condition for “input-to-state stability” (ISS) is also necessary, settling positively an open question raised by several authors during the past few years. Additional characterizations of the ISS property, including one in terms of nonlinear stability margins, are also provided.

## Relevance to your work
ISS and its Lyapunov characterizations underpin robustness certificates for tracking-error bounds under disturbances; this result is the formal backing for treating an ISS-Lyapunov function as equivalent to the ISS property itself, as used in robust tube/tracking analyses like [[@csomayshanklin2025dynamically]].

## Concepts
[[tracking-error-bound]]

## Source
- Cited by [[@csomayshanklin2025dynamically]]
- bibkeys: `sontag_characterizations_1995`
- DOI: https://doi.org/10.1016/0167-6911(94)00050-6
- URL: https://www.sciencedirect.com/science/article/pii/0167691194000506
