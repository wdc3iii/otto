---
type: paper
citekey: dai2025walk
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Dai, Min
- Compton, William D.
- Li, Junheng
- Yang, Lizhi
- Ames, Aaron D.
year: 2025
venue: RA-L
doi: null
arxiv: null
url: null
zotero: null
status: read
mine: true
pdf: attachments/@dai2025walk.pdf
---

# Walk the PLANC: Physics-Guided RL for Agile Humanoid Locomotion on Constrained Footholds

> [!info] Dai, Min; Compton, William D.; Li, Junheng; Yang, Lizhi; Ames, Aaron D. · 2025 · RA-L — **my paper**

## Abstract
Bipedal humanoid robots must precisely coordi- nate balance, timing, and contact decisions when locomoting on constrained footholds such as stepping stones, beams, and planks—even minor errors can lead to catastrophic failure. Classical optimization and control pipelines handle these con- straints well but depend on highly accurate mathematical representations of terrain geometry, making them prone to error when perception is noisy or incomplete. Meanwhile, rein- forcement learning has shown strong resilience to disturbances and modeling errors, yet end-to-end policies rarely discover the precise foothold placement and step sequencing required for discontinuous terrain. These contrasting limitations motivate approaches that guide learning with physics-based structure rather than relying purely on reward shaping. In this work, we introduce a locomotion framework in which a reduced- order stepping planner supplies dynamically consistent motion targets that steer the RL training process via Control Lyapunov Function (CLF) rewards. This combination of structured foot- step planning and data-driven adaptation produces accurate, agile, and hardware-validated stepping-stone locomotion on a humanoid robot, substantially improving reliability compared to conventional model-free reinforcement-learning baselines. The open-source code base is available at https://github. com/Zolkin1/robot_

## Summary
> [!note] Your paper — add your framing / key contribution in your own words.

## Concepts
<!-- [[03-Concepts]] links -->

## References (in otto)
- [[@acosta2023bipedal]]
- [[@acosta2025perceptive]]
- [[@bang2024rl]]
- [[@cui2024adapting]]
- [[@dai2022bipedal]]
- [[@deits2014footstep]]
- [[@duan2022learning]]
- [[@duan2022sim]]
- [[@fallon2015continuous]]
- [[@fallon2019plane]]
- [[@griffin2019footstep]]
- [[@grizzle2014models]]
- [[@gu2024advancing]]
- [[@he2025attention]]
- [[@jenelten2024dtc]]
- [[@khadiv2020walking]]
- [[@kim2025learning]]
- [[@kojio2020footstep]]
- [[@lee2024integrating]]
- [[@li2025clf]]
- [[@li2025gait]]
- [[@liao2025beyondmimic]]
- [[@liu2025opt2skill]]
- [[@nguyen20163d]]
- [[@nguyen2018dynamic]]
- [[@perrin2012fast]]
- [[@ponton2021efficient]]
- [[@schulman2017proximal]]
- [[@singh2022learning]]
- [[@suliman2025reinforcement]]
- [[@wang2025beamdojo]]
- [[@xiang2024adaptive]]
- [[@xie2020allsteps]]
- [[@xiong2022underactuated]]
- [[@yu2024learning]]
- [[@zhang2026ame]]
