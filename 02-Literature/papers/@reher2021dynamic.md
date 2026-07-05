---
type: paper
citekey: reher2021dynamic
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Reher, Jenna
year: 2021
venue: California Institute of Technology
doi: https://doi.org/10.7907/h8v0-vd47
arxiv: null
url: https://thesis.library.caltech.edu/14188/
summary: ai-draft
pdf: attachments/@reher2021dynamic.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- reher2021dynamic
---

# Dynamic Bipedal Locomotion: From Hybrid Zero Dynamics to Control Lyapunov Functions Via Experimentally Realizable Methods

> [!info] Reher, Jenna · 2021 · California Institute of Technology

## Summary
> [!note] AI-drafted from the thesis abstract — a base to refine.
**TL;DR** — Jenna Reher's Caltech PhD thesis: a unified path from hybrid zero dynamics gait synthesis to experimentally realizable control-Lyapunov-function controllers, culminating in the first CLF controller for a 3D biped (Cassie) on hardware.

**Problem** — Realizing formally-guaranteed nonlinear controllers for dynamic, underactuated bipeds — integrating modeling, trajectory planning, and feedback control — is hard to carry all the way to hardware.

**Method** — Part one develops HZD methods for gait synthesis on underactuated bipeds (including the first experimental multi-contact humanoid walking with HZD on DURUS, and compliant walking across speeds on Cassie). Part two introduces a CLF framework that combines convergence constraints with inverse dynamics and quadratic programming, gives stability analysis, and extends to a relaxed CLF formulation for practical use.

**Key results** — Reports the first successful realization of a CLF controller for a 3D biped on hardware, implemented on Cassie to track virtual constraints while regulating ground reaction forces through real-time optimization; also the first experimental multi-contact HZD humanoid walking (DURUS).

## Takeaways
- The definitive long-form treatment behind the associated CLF/HZD papers — modeling, gait library, CLF-QP, and hardware in one narrative.
- Introduces the relaxed CLF formulation that makes the guarantees tractable on real, compliant, underactuated robots.
- Two hardware firsts: multi-contact HZD humanoid walking (DURUS) and a 3D-biped CLF controller (Cassie).

## Relevance to your work
Foundational thesis for CLF/HZD-based legged locomotion with formal guarantees; the source document behind the "experimentally realizable" CLF controllers that later robust-locomotion work such as [[@csomayshanklin2024robust]] builds on and contrasts with.

## Concepts


## Source
- Cited by [[@csomayshanklin2024robust]]
- bibkeys: `reher2021dynamic`
