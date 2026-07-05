---
type: paper
citekey: grizzle2014models
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Grizzle, Jessy W.
- Chevallereau, Christine
- Sinnet, Ryan W.
- Ames, Aaron D.
year: 2014
venue: Automatica
doi: 10.1016/j.automatica.2014.04.021
arxiv: null
url: https://doi.org/10.1016/j.automatica.2014.04.021
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- grizzle_models_2014
---

# Models, feedback control, and open problems of 3D bipedal robotic walking

> [!info] Grizzle, Jessy W.; Chevallereau, Christine; Sinnet, Ryan W.; Ames, Aaron D. · 2014 · Automatica

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A survey of 3D bipedal walking that frames the biped as a hybrid dynamical system and lays out models, feedback-control design approaches, and open problems.
**Problem** — Realizing human-like stable, agile walking requires control laws matched to the biped's hybrid nature (continuous swing dynamics plus discrete impact events at touchdown), and the literature lacked a unifying treatment.
**Method** — The paper highlights model properties that most influence controller design, surveys the field, and develops two control-design approaches in depth (notably virtual constraints / hybrid zero dynamics for underactuated walking).
**Key results** — A tutorial-survey rather than an experimental paper; its contribution is the hybrid-systems framing and a catalog of open problems in 3D bipedal control.

## Takeaways
- Canonical reference for treating legged walking as a hybrid system with unilateral constraints and impulsive impacts.
- Hybrid zero dynamics / virtual constraints are presented as a principled route to provably stable underactuated gaits.
- A survey: strong for framing and problem statements, not for a single method or benchmark number.

## Relevance to your work
Foundational hybrid-systems and HZD framing that underlies model-based legged control; the classical stability lens a learning-based walking approach such as [[@dai2025walk]] is measured against.

## Abstract (from bib)
The fields of control and robotics are working toward the development of bipedal robots that can realize walking motions with the stability and agility of a human being. Dynamic models for bipeds are hybrid in nature. They contain both continuous and discrete elements, with switching events that are governed by a combination of unilateral constraints and impulse-like forces that occur at foot touchdown. Control laws for these machines must be hybrid as well. The goals of this paper are fourfold: highlight certain properties of the models which greatly influence the control law design; overview the literature; present two control design approaches in depth; and indicate some of the many open problems.

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `grizzle_models_2014`
- DOI: https://doi.org/10.1016/j.automatica.2014.04.021
