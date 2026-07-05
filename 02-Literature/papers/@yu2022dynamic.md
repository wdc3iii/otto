---
type: paper
citekey: yu2022dynamic
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Yu, Fangzhou
- Batke, Ryan
- Dao, Jeremy
- Hurst, Jonathan
- Green, Kevin
- Fern, Alan
year: 2022
venue: 2022 IEEE-RAS 21st International Conference on Humanoid Robots (Humanoids)
doi: 10.1109/Humanoids53995.2022.10000225
arxiv: null
url: https://par.nsf.gov/servlets/purl/10396739
summary: ai-draft
pdf: attachments/@yu2022dynamic.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- yu2022dynamic
---

# Dynamic bipedal turning through sim-to-real reinforcement learning

> [!info] Yu, Fangzhou; Batke, Ryan; Dao, Jeremy; Hurst, Jonathan; Green, Kevin; Fern, Alan · 2022 · 2022 IEEE-RAS 21st International Conference on Humanoid Robots (Humanoids)

## Summary
> [!note] AI-drafted from the abstract/paper metadata — a base to refine.

**TL;DR** — Trains a sim-to-real RL policy that performs dynamic bipedal turning (four-step, 90° turns) on the Cassie robot, guided by reference trajectories from a reduced single-rigid-body model.

**Problem** — Dynamic turning is a demanding maneuver for underactuated bipeds; learning such specific behaviors from reference data and transferring them reliably to hardware is difficult.

**Method** — Uses a recurrent policy to execute four-step 90° turns, trained against reference data generated from optimized single-rigid-body-model (SRBM) trajectories. Introduces a training framework using "epilogue" terminal rewards to learn specific behaviors from pre-computed trajectory data, then transfers the policy sim-to-real.

**Key results** — Successful transfer to hardware, demonstrating dynamic 90° turning on the bipedal robot Cassie.

## Takeaways
- Reference trajectories from an optimized reduced-order (single-rigid-body) model shape what the RL policy learns — a template-guided RL recipe.
- The "epilogue terminal reward" is the methodological hook for learning discrete, goal-terminating maneuvers from pre-computed trajectories.
- Recurrent policy + domain-randomized sim-to-real yields a hardware-validated turning behavior on Cassie.

## Relevance to your work
A concrete instance of reduced-order-model-guided RL for legged locomotion that transfers to hardware — relevant to reference-guided humanoid locomotion/navigation policies such as [[@terrain2026consistent]].

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `yu2022dynamic`
