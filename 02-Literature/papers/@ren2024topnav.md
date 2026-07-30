---
type: paper
citekey: ren2024topnav
tags: [navigation, locomotion]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Ren, Junli
- Liu, Yikai
- Dai, Yingru
- Long, Junfeng
- Wang, Guijin
year: 2024
venue: CoRL 2024 (PMLR v270)
doi: 10.48550/arXiv.2404.15256
arxiv: '2404.15256'
url: https://arxiv.org/abs/2404.15256
pdf: attachments/@ren2024topnav.pdf
zotero: null
status: to-read
mine: false
---

# TOP-Nav: Legged Navigation Integrating Terrain, Obstacle and Proprioception Estimation

> [!info] Junli Ren; Yikai Liu; Yingru Dai; Junfeng Long; Guijin Wang · 2024 · CoRL 2024 (PMLR v270)
> arXiv:2404.15256 (2404.15256v4, 2024-09-27) · Published on CoRL 2024

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.3 (ref `[16]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[16]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Legged robotics: reconstructing privileged information from a recurrent state*. Terrain class as an explicit estimated **module** rather than an aux head — the architectural alternative.

## Your take (your words — authoritative, not ai-draft)
> **Take:** proposal #2 (terrain class) realised as an explicit estimated module rather than an aux head — the architectural alternative worth naming when we write up the choice.

## Abstract (from arXiv)
Legged navigation is typically examined within open-world, off-road, and challenging environments.
In these scenarios, estimating external disturbances requires a complex synthesis of multi-modal
information. This underlines a major limitation in existing works that primarily focus on avoiding
obstacles. In this work, we propose TOP-Nav, a novel legged navigation framework that integrates a
comprehensive path planner with Terrain awareness, Obstacle avoidance and close-loop Proprioception.
TOP-Nav underscores the synergies between vision and proprioception in both path and motion
planning. Within the path planner, we present and integrate a terrain estimator that enables the
robot to select waypoints on terrains with higher traversability while effectively avoiding
obstacles. In the motion planning level, we not only implement a locomotion controller to track the
navigation commands, but also construct a proprioception advisor to provide motion evaluations for
the path planner. Based on the close-loop motion feedback, we make online corrections for the
vision-based terrain and obstacle estimations. Consequently, TOP-Nav achieves open-world navigation
that the robot can handle terrains or disturbances beyond the distribution of prior knowledge and
overcomes constraints imposed by visual conditions. Building upon extensive experiments conducted in
both simulation and real-world environments, TOP-Nav demonstrates superior performance in open-world
navigation compared to existing methods.

## Concepts
- [[traversability-estimation]]
- [[state-estimation]]
- [[mapless-navigation]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/2404.15256 (2404.15256v4, published 2024-04-23, updated 2024-09-27)
- DOI: https://doi.org/10.48550/arXiv.2404.15256
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.3.
