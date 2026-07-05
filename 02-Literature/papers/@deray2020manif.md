---
type: paper
citekey: deray2020manif
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Jérémie Deray
- Joan Solà
year: 2020
venue: Journal of Open Source Software
doi: 10.21105/joss.01371
arxiv: null
url: https://doi.org/10.21105/joss.01371
zotero: null
summary: ai-draft
pdf: attachments/@deray2020manif.pdf
status: to-read
mine: false
bibkeys:
- Deray-20-JOSS
---

# Manif: A micro Lie theory library for state estimation in robotics applications

> [!info] Jérémie Deray; Joan Solà · 2020 · Journal of Open Source Software

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — `manif` is a header-only C++ micro Lie theory library providing the common Lie-group operations needed for state estimation in robotics.
**Problem** — Proper, uncertainty- and manifold-aware formulation of estimation problems requires convenient tooling for the Lie groups on which robot states evolve; hand-rolling this is error-prone.
**Method** — An Eigen-style, header-only library (single Eigen dependency, C++11) using templated base classes and static polymorphism, so generic code avoids pointer-arithmetic overhead. Implements SO(2)/SO(3) and SE(2)/SE(3) with clean interfaces and is extensible to further Lie groups; math foundations follow Solà et al.'s micro Lie theory.
**Key results** — A lightweight, easy-to-integrate library for on-manifold state representation and its Jacobians (a software contribution rather than an empirical result).

## Takeaways
- Practical, dependency-light implementation of the "estimation on manifolds" formalism (SO(3)/SE(3) with proper tangent-space uncertainty).
- Header-only + static polymorphism keeps it fast and easy to drop into existing robotics code.

## Relevance to your work
Cited in [[@csomayshanklin2024robust]] (and [[@hierarchies2025motion]]) as the implementation tooling for Lie-group state representations — the SE(3)/SO(3) machinery underlying geometric state estimation and control on manifolds.

## Concepts
## Source
- Cited by [[@csomayshanklin2024robust]], [[@hierarchies2025motion]]
- bibkeys: `Deray-20-JOSS`
- DOI: https://doi.org/10.21105/joss.01371
