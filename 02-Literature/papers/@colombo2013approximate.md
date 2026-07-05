---
type: paper
citekey: colombo2013approximate
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- A. Colombo
- A. Girard
year: 2013
venue: ECC
doi: 10.23919/ecc.2013.6669178
arxiv: null
url: https://ieeexplore.ieee.org/document/6669178
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- GirardECC13
---

# An approximate abstraction approach to safety control of differentially flat systems

> [!info] A. Colombo; A. Girard · 2013 · ECC

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Designs a safety supervisor for differentially flat systems by building an approximate abstraction directly on the flat-output space, giving a simpler, more flexible controller than prior abstraction-based approaches.
**Problem** — Abstraction-based safety supervision for constrained nonlinear systems is computationally heavy; building the abstraction over the full state space is expensive and inflexible.
**Method** — Exploits differential flatness to define the abstraction on the (lower-dimensional) flat output rather than the full state, which simplifies abstraction construction and reduces the computational complexity of the resulting supervisor; approximate simulation techniques relate the abstraction back to the true system.
**Key results** — Yields a simpler and more flexible supervisor than earlier solutions; validated on an eight-dimensional nonlinear planar crane model.

## Takeaways
- Doing the abstraction on the flat output is the key move — it shrinks the space the supervisor reasons over while preserving a certified relation to the plant.
- Differential flatness is the enabling assumption; approximate simulation supplies the plan-to-plant error guarantee.
- Trades some conservatism for a large drop in supervisor computation, making abstraction-based safety more practical.

## Relevance to your work
Abstraction-on-the-flat-output is a low-dimensional-model route to safety with a certified relation to the plant, complementary to the CBF/tube machinery in [[@cohen2025safety]] — a reminder that flatness offers another lever for cheap, safe reduced-order planning.

## Concepts
[[reduced-order-model]] [[tracking-error-bound]]

## Source
- Cited by [[@cohen2025safety]]
- bibkeys: `GirardECC13`
