---
type: paper
citekey: sontag1999lyapunov
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Sontag, Eduardo D.
year: 1999
venue: Open Problems in Mathematical Systems and Control Theory
doi: 10.1007/978-1-4471-0807-8_40
arxiv: null
url: https://doi.org/10.1007/978-1-4471-0807-8_40
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- sontag_control-lyapunov_1999
---

# Control-Lyapunov functions

> [!info] Sontag, Eduardo D. · 1999 · Open Problems in Mathematical Systems and Control Theory

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A short survey/open-problems piece framing control-Lyapunov functions as the central tool for nonlinear stabilization and laying out what remains unresolved.
**Problem** — Stabilization of finite-dimensional deterministic nonlinear systems remains far from settled (identified in late-1980s reports as a top open problem in control), unlike the well-understood linear case.
**Method** — Reviews the CLF concept — a Lyapunov function whose decrease can be enforced by some choice of control — as the unifying object for regulation/tracking-recast-as-stabilization, and poses open questions around its existence, construction, and use.
**Key results** — Positions CLFs (and constructive results such as Sontag's universal formula) as the backbone of nonlinear feedback stabilization, while flagging gaps that motivate continued research. (Open-problems essay; no experiments.)

## Takeaways
- Tracking and regulation problems can typically be recast as stabilization of an error signal, making CLFs broadly applicable.
- Existence of a CLF is equivalent to (smooth) stabilizability, but constructing one for a given system is the hard, still-open part.
- A concise, citable framing of why CLFs matter — companion to Sontag's 1989 universal-formula result.

## Abstract (from bib)
The main objective of control is to modify the behavior of a dynamical system, typically with the purpose of regulating certain variables or of tracking desired signals. Often, either stability of the closed-loop system is an explicit requirement, or else the problem can be recast in a form that involves stabilization (e.g., of an error signal). For linear systems, the associated problems can now be treated fairly satisfactorily, but in the nonlinear case the area is still far from being settled. Both of the late 1980s reports [9] and [18], with dealt with challenges and future directions for research in control theory, identified the problem of stabilization of finite-dimensional deterministic systems as one of the most important open problems in nonlinear control. We discuss some questio

## Relevance to your work
Establishes the CLF as the organizing object for nonlinear stabilization, the theoretical footing for the constructive controller designs in [[@compton2024constructive]].

## Concepts


## Source
- Cited by [[@compton2024constructive]]
- bibkeys: `sontag_control-lyapunov_1999`
- DOI: https://doi.org/10.1007/978-1-4471-0807-8_40
