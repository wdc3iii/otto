---
type: paper
citekey: galloway2015torque
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Galloway, Kevin
- Sreenath, Koushil
- Ames, Aaron D.
- Grizzle, Jessy W.
year: 2015
venue: IEEE Access
doi: 10.1109/ACCESS.2015.2419630
arxiv: null
url: https://doi.org/10.1109/ACCESS.2015.2419630
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- galloway_torque_2015
---

# Torque Saturation in Bipedal Robotic Walking Through Control Lyapunov Function-Based Quadratic Programs

> [!info] Galloway, Kevin; Sreenath, Koushil; Ames, Aaron D.; Grizzle, Jessy W. · 2015 · IEEE Access
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A CLF-QP controller that embeds user-defined torque (actuator) bounds directly, so a biped degrades gracefully instead of failing under saturation.
**Problem** — CLF-based controllers for periodic bipedal gaits ignore actuator saturation; hard input limits can destabilize walking.
**Method** — Formulates the CLF-based controller as a quadratic program (QP) with input bounds and a family of user-defined constraints imposed online, trading off strict CLF decrease against feasibility so performance degrades gradually as limits tighten.
**Key results** — Experimentally validated on the bipedal robot MABEL: the robot keeps walking under increasingly stringent torque bounds, with graceful performance degradation.

## Takeaways
- The CLF-QP relaxes the Lyapunov constraint to respect hard input limits — a template that generalizes to CBF-QPs and other pointwise-optimal safety filters.
- Graceful degradation under saturation, demonstrated on hardware, not just simulation.
- Builds on prior CLF gait-stabilization work; the QP is the mechanism for injecting real actuator constraints.

## Relevance to your work
Canonical CLF-QP-with-input-constraints reference underpinning safety-critical and torque-limited controller synthesis for legged robots. See [[@cohen2025safety]].

## Abstract (from bib)
This paper presents a novel method to address the actuator saturation for nonlinear hybrid systems by directly incorporating user-deﬁned input bounds in a controller design. In particular, we consider the application of bipedal walking and show that our method [based on a quadratic programming (QP) implementation of a control Lyapunov function (CLF)-based controller] enables a gradual performance degradation while still continuing to walk under increasingly stringent input bounds. We draw on our previous work, which has demonstrated the effectiveness of the CLF-based controllers for stabilizing periodic gaits for biped walkers. This paper presents a framework, which results in more effective handling of control saturations and provides a means for incorporating a whole family of user-deﬁne

## Concepts

## Source
- Cited by [[@olkin2026stability]]
- bibkeys: `galloway_torque_2015`
- DOI: https://doi.org/10.1109/ACCESS.2015.2419630
