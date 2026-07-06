---
type: paper
citekey: nubert2025holistic
tags: [navigation, method]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Nubert, Julian
- Tuna, Turcan
- Frey, Jonas
- Cadena, Cesar
- Kuchenbecker, Katherine J.
- Khattak, Shehryar
- Hutter, Marco
year: 2025
venue: arXiv
doi: 10.48550/arXiv.2504.06479
arxiv: '2504.06479'
url: http://arxiv.org/abs/2504.06479
zotero: null
summary: ai-draft
pdf: attachments/@nubert2025holistic.pdf
status: to-read
mine: false
bibkeys:
- nubertHolisticFusionTask2025
---

# Holistic Fusion: Task- and Setup-Agnostic Robot Localization and State Estimation with Factor Graphs

> [!info] Julian Nubert; Turcan Tuna; Jonas Frey; Cesar Cadena; Katherine J. Kuchenbecker; Shehryar Khattak; Marco Hutter · 2025 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — An open-source factor-graph sensor-fusion framework that jointly estimates local and global robot state plus arbitrary dynamic context variables, giving low-latency smooth local estimation and low-drift global localization without per-scenario redesign.
**Problem** — Mobile robots need both low-latency local motion estimation (dynamic maneuvers) and accurate global localization (wayfinding), but most sensor-fusion approaches are built for specific setups.
**Method** — Holistic Fusion (HF): a factor-graph formulation combining estimation of (i) local + global robot state and (ii) an unlimited number of dynamic context variables, with automatic reference-frame alignment. Absolute, local, and landmark measurements in different frames are fused as explicit states whose evolution is modeled as random walks; particular attention to local smoothness/consistency to avoid belief jumps.
**Key results** — Low-latency, smooth online state estimation on typical robot hardware with low-drift global localization at IMU rate; demonstrated in five real-world scenarios across three robotic platforms with distinct task requirements (no numeric figures read).

## Takeaways
- Unifies local + global state and arbitrary dynamic context variables in a single factor graph, with automatic frame alignment.
- Random-walk modeling lets it fuse measurements expressed in different reference frames as explicit states.
- Prioritizes smoothness/consistency to prevent state-belief jumps; released open source.

## Relevance to your work
Relevant infrastructure for navigation autonomy: a general state-estimation/localization backbone that supplies the smooth local + drift-free global state a legged navigation and control stack consumes. Tangential to your control-theory core but directly useful as the estimation layer under perceptive locomotion on the G1.

## Abstract (from bib)
Seamless operation of mobile robots in challenging environments requires low-latency local motion estimation (e.g., dynamic maneuvers) and accurate global localization (e.g., wayfinding). While most existing sensor-fusion approaches are designed for specific scenarios, this work introduces a flexible open-source solution for task- and setup-agnostic multimodal sensor fusion that is distinguished by its generality and usability. Holistic Fusion formulates sensor fusion as a combined estimation problem of i) the local and global robot state and ii) a (theoretically unlimited) number of dynamic context variables, including automatic alignment of reference frames; this formulation fits countless real-world applications without any conceptual modifications. The proposed factor-graph solution enables the direct fusion of an arbitrary number of absolute, local, and landmark measurements expressed with respect to different reference frames by explicitly including them as states in the optimization and modeling their evolution as random walks. Moreover, local smoothness and consistency receive particular attention to prevent jumps in the robot state belief. HF enables low-latency and smooth online state estimation on typical robot hardware while simultaneously providing low-drift global localization at the IMU measurement rate. The efficacy of this released framework is demonstrated in five real-world scenarios on three robotic platforms, each with distinct task requirements.

## Concepts
- [[state-estimation]] — task-/setup-agnostic robot localization and sensor fusion.

## Source
- bibkeys: `nubertHolisticFusionTask2025`
- arXiv: http://arxiv.org/abs/2504.06479
- DOI: https://doi.org/10.48550/arXiv.2504.06479
- URL: http://arxiv.org/abs/2504.06479
