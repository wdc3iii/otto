---
type: paper
citekey: sharf2021assume
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Miel Sharf
- Bart Besselink
- Adam Molin
- Qiming Zhao
- Karl Henrik Johansson
year: 2021
venue: IFAC-PapersOnLine
doi: https://doi.org/10.1016/j.ifacol.2021.08.469
arxiv: null
url: https://doi.org/10.1016/j.ifacol.2021.08.469
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- SHARF202125
- Sharf
---

# Assume/Guarantee Contracts for Dynamical Systems: Theory and Computational Tools

> [!info] Miel Sharf; Bart Besselink; Adam Molin; Qiming Zhao; Karl Henrik Johansson · 2021 · IFAC-PapersOnLine

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Develops an assume/guarantee contract theory for discrete-time dynamical control systems, with linear-constraint contracts and LP-based tools for verifying satisfaction and refinement.
**Problem** — Verifying that large, multi-component engineering systems meet their specifications is hard; most formal methods scale only to moderate size, motivating a modular specification framework.
**Method** — Formulates contracts as assumptions on a system's input and guarantees on its output. Specializing to contracts defined by linear constraints, it derives efficient linear-programming procedures to check both contract satisfaction (does a system meet its contract) and refinement (does one contract imply another).
**Key results** — Demonstrated on a two-vehicle autonomous-driving example, proving a safety specification.

## Takeaways
- Contracts give a compositional way to certify interconnected systems: verify components against local assume/guarantee pairs instead of the monolithic whole.
- Restricting to linear-constraint contracts makes verification and refinement tractable via LP.

## Relevance to your work
Cited in [[@contract2025theory]] as a direct theoretical antecedent — assume/guarantee contracts are the formalism for compositional, layered control where a high-level controller assumes guarantees provided by a lower-level tracking layer.

## Abstract (from bib)
Modern engineering systems include many components of different types and functions. Verifying that these systems satisfy given specifications can be an arduous task, as most formal verification methods are limited to systems of moderate size. Recently, contract theory has been proposed as a modular framework for defining specifications. In this paper, we present a contract theory for discrete-time dynamical control systems relying on assume/guarantee contracts, which prescribe assumptions on the input of the system and guarantees on the output. We then focus on contracts defined by linear constraints, and develop efficient computational tools for verification of satisfaction and refinement based on linear programming. We exemplify these tools in a simulation example, proving a certain saf

## Concepts
## Source
- Cited by [[@contract2025theory]], [[@hierarchies2025motion]]
- bibkeys: `SHARF202125`, `Sharf`
- DOI: https://doi.org/https://doi.org/10.1016/j.ifacol.2021.08.469
