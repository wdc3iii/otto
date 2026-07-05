---
type: paper
citekey: csomayshanklin2021episodic
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Csomay-Shanklin, Noel
- Cosner, Ryan K
- Dai, Min
- Taylor, Andrew J
- Ames, Aaron D
year: 2021
venue: Learning for Dynamics and Control
doi: null
arxiv: '2105.01697'
url: https://arxiv.org/abs/2105.01697
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@csomayshanklin2021episodic.pdf
bibkeys:
- csomay2021episodic
---

# Episodic learning for safe bipedal locomotion with control barrier functions and projection-to-state safety

> [!info] Csomay-Shanklin, Noel; Cosner, Ryan K; Dai, Min; Taylor, Andrew J; Ames, Aaron D · 2021 · Learning for Dynamics and Control

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Combines episodic learning with control barrier functions for bipedal locomotion, using projection-to-state safety to learn the model uncertainty that corrupts CBF safety guarantees on hardware.
**Problem** — CBF safety guarantees hold only under perfect model knowledge, an assumption violated on real robots; model error degrades the barrier condition.
**Method** — The authors pair projection-to-state safety (PSSf) with an episodic machine-learning framework that iteratively learns how model uncertainty affects the barrier functions from collected experience.
**Key results** — Demonstrated in simulation and on the AMBER-3M bipedal robot for the stepping-stone problem, which demands precise foot placement during dynamic walking.

## Takeaways
- Frames model uncertainty specifically through its effect on the barrier function, not on the full dynamics — projection-to-state safety is the bridge.
- Episodic (data-collect-then-update) learning loop makes the safety filter progressively more reliable on hardware.
- Validated on a hard precise-footstep task, a locomotion analogue of navigating tight constraints.

## Relevance to your work
A direct precedent for learning-in-the-loop safety on legged hardware, closely aligned with your learned-tracking-error and safety work such as [[@compton2025learning]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025learning]]
- bibkeys: `csomay2021episodic`
