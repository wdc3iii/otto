---
type: paper
citekey: xiong2022underactuated
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Xiong, Xiaobin
- Ames, Aaron
year: 2022
venue: IEEE Transactions on Robotics
doi: 10.1109/TRO.2022.3150219
arxiv: null
url: https://doi.org/10.1109/TRO.2022.3150219
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- xiong_3-d_2022
---

# 3-D Underactuated Bipedal Walking via H-LIP Based Gait Synthesis and Stepping Stabilization

> [!info] Xiong, Xiaobin; Ames, Aaron · 2022 · IEEE Transactions on Robotics

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A hybrid-linear-inverted-pendulum (H-LIP) reduced-order model that synthesizes and provably stabilizes 3-D underactuated bipedal walking through step-to-step (S2S) stepping control, demonstrated on Cassie hardware.
**Problem** — Underactuated 3-D bipeds (point/passive feet) are hard to gait-synthesize and stabilize; the paper seeks a principled, hardware-realizable template that captures both the underactuated and actuated parts of walking.
**Method** — The H-LIP template captures the essential dynamics; walking gaits are synthesized directly from it. The authors characterize the H-LIP's periodic orbits and derive stepping stabilization via its S2S dynamics, then use the H-LIP S2S to approximate the CoM horizontal S2S dynamics of the full robot. A H-LIP-based stepping controller outputs desired step sizes; realizing them yields dynamic, stable walking.
**Key results** — Full evaluation in simulation and on the 3-D underactuated biped Cassie, demonstrating versatile and robust dynamic walking behaviors.

## Takeaways
- H-LIP is a reduced-order template whose analytically characterized S2S dynamics give provable stepping stabilization — a clean bridge from a linear template to a complex underactuated robot.
- Foot placement (step size) is the stabilizing control input; the S2S approximation error between H-LIP and the full robot bounds tracking performance.
- Validated end-to-end on Cassie hardware, not just simulation — a key reference point for template-based locomotion.

## Relevance to your work
Foundational reduced-order-model + step-to-step approach for underactuated legged locomotion that grounds template-based synthesis; directly relevant to [[@dai2025walk]] and to reduced-order tracking-guarantee lines of work.

## Abstract (from bib)
In this article, we holistically present a hybrid-linear inverted pendulum (H-LIP) based approach for synthesizing and stabilizing 3-D foot-underactuated bipedal walking, with an emphasis on thorough hardware realization. The H-LIP is proposed to capture the essential components of the underactuated and actuated part of the robotic walking. The robot walking gait is then directly synthesized based on the H-LIP. We comprehensively characterize the periodic orbits of the H-LIP and provably derive the stepping stabilization via its step-to-step (S2S) dynamics, which is then utilized to approximate the S2S dynamics of the horizontal state of the center of mass of the robotic walking. The approximation facilities a H-LIP based stepping controller to provide desired step sizes to stabilize the r

## Concepts
[[reduced-order-model]] [[tracking-error-bound]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `xiong_3-d_2022`
- DOI: https://doi.org/10.1109/TRO.2022.3150219
