---
type: paper
citekey: incer2024layered
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Incer, Inigo
- Csomay-Shanklin, Noel
- Ames, Aaron D
- Murray, Richard M
year: 2024
venue: IEEE Control Systems Letters
doi: 10.1109/lcsys.2024.3410150
arxiv: null
url: https://doi.org/10.1109/lcsys.2024.3410150
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- incer_specifying_2024
---

# Layered control systems operating on multiple clocks

> [!info] Incer, Inigo; Csomay-Shanklin, Noel; Ames, Aaron D; Murray, Richard M · 2024 · IEEE Control Systems Letters

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces Multiclock Logic (MCL) and assume-guarantee contracts to formally prove global stability of layered control architectures whose components run on different clocks/timescales.
**Problem** — Layered control stacks are built by interconnecting components operating at multiple timescales, but this composition is typically heuristic, with no formal way to specify each component's requirements from its own local clock or to certify the assembled system.
**Method** — The authors define a new logic, Multiclock Logic (MCL), letting each component express requirements from the point of view of its local clock, which promotes independent design and reuse. Assume-guarantee contracts written in MCL then compose the components' stability properties into a global stability guarantee.
**Key results** — They apply the framework to the classic architecture of model predictive control (MPC) layered on top of feedback linearization and prove overall stability of the composed system.

## Takeaways
- Formalizes the timescale separation that layered/hierarchical control relies on, turning a heuristic into a contract-based proof obligation.
- Assume-guarantee contracts let component stability compose into system stability, enabling independent design and reuse across clock domains.
- Worked case is MPC-over-feedback-linearization, the canonical two-layer stack.

## Relevance to your work
Directly supports contract-based reasoning about multi-rate layered controllers; the MPC-on-feedback-linearization stability result is the formal analogue of the layered locomotion stacks you study. See [[@contract2025theory]].

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `incer_specifying_2024`
