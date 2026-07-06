---
type: paper
citekey: duan2024vision
tags: [locomotion, rl]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Duan, Helei
- Pandit, Bikram
- Gadde, Mohitvishnu S.
- van Marum, Bart
- Dao, Jeremy
- Kim, Chanho
- Fern, Alan
year: 2024
venue: arXiv
doi: 10.48550/arXiv.2309.14594
arxiv: '2309.14594'
url: http://arxiv.org/abs/2309.14594
zotero: null
summary: ai-draft
pdf: attachments/@duan2024vision.pdf
status: to-read
mine: false
bibkeys:
- duanLearningVisionBasedBipedal2024
---

# Learning Vision-Based Bipedal Locomotion for Challenging Terrain

> [!info] Helei Duan; Bikram Pandit; Mohitvishnu S. Gadde; Bart van Marum; Jeremy Dao; Chanho Kim; Alan Fern · 2024 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A fully-learned vision-based controller lets a bipedal robot anticipate and adapt to local terrain while holding commanded speed/direction, with sim-to-real transfer and no explicit pose estimation.
**Problem** — Proprioception-only ("blind") RL bipedal controllers are robust on moderate terrain but fail where the robot must anticipate and adapt to local terrain, which requires visual perception.
**Method** — Train a controller in simulation on a robot-local-frame heightmap; then collect simulation data to train a heightmap predictor whose input is a history of depth images and robot states; use domain randomization to enable sim-to-real transfer with no explicit pose estimation and no real-world fine-tuning.
**Key results** — Claimed to be the first sim-to-real learning for vision-based bipedal locomotion over challenging terrains; successful sim-to-real transfer demonstrated (no numeric figures read).

## Takeaways
- Two-stage decomposition: a heightmap-conditioned controller plus a separate learned heightmap predictor from depth-image + state history.
- Domain randomization alone carries the transfer; no explicit pose estimation and no real-world fine-tuning needed.

## Relevance to your work
Directly on-line with perceptive/terrain-aware RL locomotion for legged systems and sim-to-real transfer — the bipedal, vision-conditioned setting is a close analogue to perceptive locomotion on the G1.

## Abstract (from bib)
Reinforcement learning (RL) for bipedal locomotion has recently demonstrated robust gaits over moderate terrains using only proprioceptive sensing. However, such blind controllers will fail in environments where robots must anticipate and adapt to local terrain, which requires visual perception. In this paper, we propose a fully-learned system that allows bipedal robots to react to local terrain while maintaining commanded travel speed and direction. Our approach first trains a controller in simulation using a heightmap expressed in the robot's local frame. Next, data is collected in simulation to train a heightmap predictor, whose input is the history of depth images and robot states. We demonstrate that with appropriate domain randomization, this approach allows for successful sim-to-real transfer with no explicit pose estimation and no fine-tuning using real-world data. To the best of our knowledge, this is the first example of sim-to-real learning for vision-based bipedal locomotion over challenging terrains.

## Concepts
- [[rl-for-legged-locomotion]]
- [[sim-to-real-transfer]]
- [[traversability-estimation]]

## Source
- bibkeys: `duanLearningVisionBasedBipedal2024`
- arXiv: http://arxiv.org/abs/2309.14594
- DOI: https://doi.org/10.48550/arXiv.2309.14594
- URL: http://arxiv.org/abs/2309.14594
