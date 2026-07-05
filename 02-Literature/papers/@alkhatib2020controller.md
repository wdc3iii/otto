---
type: paper
citekey: alkhatib2020controller
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Al Khatib, Mohammad
- Zamani, Majid
year: 2020
venue: 2020 American Control Conference (ACC)
doi: 10.23919/ACC45564.2020.9147757
arxiv: null
url: https://doi.org/10.23919/ACC45564.2020.9147757
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- Alkhatib
---

# Controller synthesis for interconnected systems using parametric assume-guarantee contracts

> [!info] Al Khatib, Mohammad; Zamani, Majid · 2020 · 2020 American Control Conference (ACC)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.

**TL;DR** — Synthesizes per-component controllers enforcing parametric assume-guarantee contracts and shows that a small-gain-like condition on the parameter sequence lifts local contracts to a contract for the whole interconnected system.

**Problem** — Compositional controller synthesis for interconnected systems: how to guarantee a global behavioral contract by reasoning only about individual components rather than the monolithic composed system.

**Method** — Parametric assume-guarantee contracts (AGC) encode component behaviors over parameter domains. A controller is synthesized separately for each component to satisfy its own parametric AGC; a mapping then generates the sequence of parameters for which the component contracts hold after interconnection. If a small-gain-like condition on that parameter sequence holds, a parametric AGC is declared for the interconnected system.

**Key results** — Recovers the classical small-gain theorem for BIBO stability as a special case, exposing the link between assume-guarantee reasoning and the small-gain approach; illustrated on a large-scale transportation-system example.

## Takeaways
- Bridges assume-guarantee contract reasoning and classical small-gain stability — the latter drops out as a special case.
- Parameterizing contracts is the key device that makes local guarantees composable across an interconnection.
- Scales the reasoning to large interconnected systems by avoiding monolithic synthesis.

## Relevance to your work
Foundational compositional-synthesis machinery for the assume-guarantee contract framework used in layered control; connects to [[@contract2025theory]].

## Concepts



## Source
- Cited by [[@contract2025theory]]
- bibkeys: `Alkhatib`
- DOI: https://doi.org/10.23919/ACC45564.2020.9147757
