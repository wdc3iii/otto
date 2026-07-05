---
type: paper
citekey: agrawal2017discrete
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Agrawal, Ayush
- Sreenath, Koushil
year: 2017
venue: 'Robotics: Science and Systems'
doi: 10.15607/RSS.2017.XIII.073
arxiv: null
url: http://www.roboticsproceedings.org/rss13/p73.html
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@agrawal2017discrete.pdf
bibkeys:
- agrawal2017discrete
---

# Discrete control barrier functions for safety-critical control of discrete systems with application to bipedal robot navigation.

> [!info] Agrawal, Ayush; Sreenath, Koushil · 2017 · Robotics: Science and Systems

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Extends control barrier functions from continuous time to discrete-time nonlinear systems and uses them to keep a 3D bipedal robot safe while navigating among moving obstacles.
**Problem** — CBFs were developed for continuous-time systems; discrete-time systems (and the sampled, step-based nature of bipedal navigation with time-varying safety constraints) needed a discrete analogue.
**Method** — The authors define and analyze two formulations of discrete control barrier functions derived from their continuous-time counterparts. Unlike the continuous case (a QP), the resulting safety filter is in general a nonlinear program, which under certain conditions reduces to a quadratically constrained quadratic program (QCQP).
**Key results** — They apply the framework to navigate a high-dimensional 3D bipedal robot through environments with moving obstacles imposing time-varying safety-critical constraints (qualitative demonstration; no benchmark numbers noted).

## Takeaways
- Discrete CBFs give a principled safety filter for sampled/step-based systems, but the optimization is an NP/QCQP rather than the clean continuous-time QP.
- Formulating enforcement per discrete step suits step-to-step bipedal navigation and time-varying obstacle constraints.
- Foundational reference for discrete-time and step-level safety guarantees in legged locomotion.

## Relevance to your work
This is a core reference for enforcing safety constraints at the discrete/footstep level for bipedal robots — directly relevant to safety-critical locomotion and the barrier-function machinery in [[@cohen2025safety]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `agrawal2017discrete`
