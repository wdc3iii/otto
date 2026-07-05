---
type: paper
citekey: jiang2001input
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Zhong-Ping Jiang
- Yuan Wang
year: 2001
venue: Automatica
doi: https://doi.org/10.1016/S0005-1098(01)00028-0
arxiv: null
url: null
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- discrete_ISS
---

# Input-to-state stability for discrete-time nonlinear systems

> [!info] Zhong-Ping Jiang; Yuan Wang · 2001 · Automatica

## Summary
> [!note] AI-drafted from the abstract — a base to refine.

**TL;DR** — Extends the input-to-state stability (ISS) framework from continuous-time to discrete-time nonlinear systems, with equivalent characterizations and small-gain theorems.

**Problem** — ISS is a foundational tool for reasoning about how bounded inputs/disturbances bound the state in continuous-time nonlinear systems, but a systematic discrete-time counterpart was lacking.

**Method** — Shows that most continuous-time ISS results carry over to discrete time, introduces several equivalent characterizations of ISS, and proves two ISS small-gain theorems for nonlinear and interconnected discrete-time systems. Also discusses ISS stabilizability and draws comparisons with the continuous-time case.

**Key results** — Establishes the equivalent characterizations and the two small-gain theorems, giving the discrete-time analogue of the continuous-time ISS machinery for stability/stabilization analysis.

## Takeaways
- Provides the discrete-time ISS toolbox (Lyapunov-style characterizations + small-gain composition) that underpins robustness arguments for sampled/discrete controllers.
- Small-gain theorems for interconnected systems are the key lever for certifying stability of cascaded or layered discrete-time systems.
- Purely theoretical; results mirror the continuous-time framework rather than exposing fundamentally new phenomena.

## Relevance to your work
Discrete-time ISS and its small-gain theorems give the formal basis for bounding tracking error of a discretely-updated tracking layer under bounded planner "inputs" — the kind of layered guarantee [[@hierarchies2025motion]] leans on.

## Abstract (from bib)
In this work we study the input-to-state stability (iss) property for discrete-time nonlinear systems. It is shown that most iss results for continuous-time nonlinear systems in the current literature can be extended to the discrete-time case. Several equivalent characterizations of iss are introduced and two iss small-gain theorems are proved for nonlinear and interconnected discrete-time systems. ISS stabilizability is discussed and comparisons with the continuous-time case are made. As in the continuous time framework, where the notion iss found wide applications, we expect that this notion will provide a useful tool in areas related to stability and stabilization for nonlinear discrete time systems as well.

## Concepts
[[tracking-error-bound]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `discrete_ISS`
- DOI: https://doi.org/https://doi.org/10.1016/S0005-1098(01)00028-0
