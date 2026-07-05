---
type: paper
citekey: xiongnd3d
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Xiong, Xiaobin
- Ames, Aaron
year: null
venue: null
doi: 10.48550/arXiv.2101.09588
arxiv: '2101.09588'
url: http://arxiv.org/abs/2101.09588
summary: ai-draft
pdf: attachments/@xiongnd3d.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- xiong3DUnderactuatedBipedal2021
---

# 3D Underactuated Bipedal Walking via H-LIP Based Gait Synthesis and Stepping Stabilization

> [!info] Xiong, Xiaobin; Ames, Aaron · n.d. · —

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — Synthesizes and stabilizes 3D foot-underactuated bipedal walking using a Hybrid-Linear Inverted Pendulum (H-LIP) template, validated on Cassie hardware.

**Problem** — Underactuated bipeds (point/line feet) lack ankle authority, so gait synthesis and step-to-step stabilization must come from foot placement rather than ankle torque; a principled, hardware-realizable template is needed.

**Method** — Proposes the H-LIP, which captures both the actuated and underactuated components of walking. The gait is synthesized directly from the H-LIP; its periodic orbits are characterized and a stepping stabilization is provably derived from the H-LIP step-to-step (S2S) dynamics. This S2S model approximates the actual S2S dynamics of the robot's horizontal COM state, and an H-LIP-based controller then prescribes desired step sizes to stabilize walking.

**Key results** — Demonstrated in simulation and on the Cassie robot, showing dynamic walking with high versatility and robustness.

## Takeaways
- The H-LIP is a reduced-order template whose closed-form S2S dynamics give provable stepping stabilization via foot placement — a clean template-to-hardware pipeline.
- The gap between H-LIP and full-robot walking is contained in an error-invariant set, so tracking the template yields bounded actual-state error.
- Assumes the horizontal COM behaves like the linear pendulum model; accuracy of the S2S approximation bounds achievable performance.

## Relevance to your work
The H-LIP is a canonical reduced-order model for underactuated bipedal locomotion, and its S2S-based stepping stabilization with an error-invariant set is a direct precursor to reference-guided and terrain-consistent locomotion pipelines like [[@terrain2026consistent]].

## Abstract (from bib)
In this paper, we holistically present a Hybrid-Linear Inverted Pendulum (H-LIP) based approach for synthesizing and stabilizing 3D foot-underactuated bipedal walking, with an emphasis on thorough hardware realization. The H-LIP is proposed to capture the essential components of the underactuated and actuated part of the robotic walking. The robot walking gait is then directly synthesized based on the H-LIP. We comprehensively characterize the periodic orbits of the H-LIP and provably derive the stepping stabilization via its step-to-step (S2S) dynamics, which is then utilized to approximate the S2S dynamics of the horizontal state of the center of mass (COM) of the robotic walking. The approximation facilities a H-LIP based stepping controller to provide desired step sizes to stabilize th

## Concepts
[[reduced-order-model]] · [[tracking-error-bound]]

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `xiong3DUnderactuatedBipedal2021`
- arXiv: https://arxiv.org/abs/2101.09588
- DOI: https://doi.org/10.48550/arXiv.2101.09588
- URL: http://arxiv.org/abs/2101.09588
