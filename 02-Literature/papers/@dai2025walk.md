---
type: paper
citekey: dai2025walk
tags: [rl, locomotion, control]
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
summary: ai-draft
pdf: attachments/@dai2025walk.pdf
---

# Walk the PLANC: Physics-Guided RL for Agile Humanoid Locomotion on Constrained Footholds

> [!info] Dai, Min; Compton, William D.; Li, Junheng; Yang, Lizhi; Ames, Aaron D. · 2025 · RA-L — **my paper**

## Abstract
Bipedal humanoid robots must precisely coordi- nate balance, timing, and contact decisions when locomoting on constrained footholds such as stepping stones, beams, and planks—even minor errors can lead to catastrophic failure. Classical optimization and control pipelines handle these con- straints well but depend on highly accurate mathematical representations of terrain geometry, making them prone to error when perception is noisy or incomplete. Meanwhile, rein- forcement learning has shown strong resilience to disturbances and modeling errors, yet end-to-end policies rarely discover the precise foothold placement and step sequencing required for discontinuous terrain. These contrasting limitations motivate approaches that guide learning with physics-based structure rather than relying purely on reward shaping. In this work, we introduce a locomotion framework in which a reduced- order stepping planner supplies dynamically consistent motion targets that steer the RL training process via Control Lyapunov Function (CLF) rewards. This combination of structured foot- step planning and data-driven adaptation produces accurate, agile, and hardware-validated stepping-stone locomotion on a humanoid robot, substantially improving reliability compared to conventional model-free reinforcement-learning baselines. The open-source code base is available at https://github. com/Zolkin1/robot_

## Summary
> [!note] AI-drafted from the abstract/intro — a base to refine or replace with your own framing.

**TL;DR** — **PLANC**: physics-guided RL for humanoid locomotion on *constrained footholds* (stepping stones/beams), where a reduced-order stepping planner supplies dynamically consistent targets that steer RL training via **CLF rewards**.
**Problem** — Stepping-stone terrain imposes hard contact-location/timing constraints (a misstep = failure); model-based pipelines need accurate terrain models, while end-to-end RL rarely finds precise foothold/step sequencing.
**Method** — A reduced-order stepping planner (LIP-style) produces dynamically consistent motion targets; a Control-Lyapunov-Function reward guides the RL policy toward them — structured footstep planning + data-driven adaptation.
**Key results** — Accurate, agile, **hardware-validated stepping-stone locomotion**, substantially more reliable than model-free RL baselines.

## Takeaways
- Physics-structured guidance (planner + CLF reward) beats pure reward shaping for precise, discontinuous-terrain stepping.
- Combines the robustness of RL with the precision of model-based footstep planning.

## Where it sits in my work
Applies the CLF-guided-RL rewards analyzed in [[@olkin2026stability]]; a constrained-terrain sibling of the perceptive nav in [[@terrain2026consistent]].

## Concepts
- [[rl-for-legged-locomotion]] · [[control-lyapunov-function]] · [[reduced-order-model]] · [[control-barrier-function]] · _to add:_ footstep-planning
- Map: [[learning-based-locomotion]]

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
