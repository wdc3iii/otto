---
type: paper
citekey: hoeller2024anymal
tags: [locomotion, navigation, rl]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Hoeller, David
- Rudin, Nikita
- Sako, Dhionis
- Hutter, Marco
year: 2024
venue: Science Robotics
doi: 10.1126/scirobotics.adi7566
arxiv: null
url: https://www.science.org/doi/10.1126/scirobotics.adi7566
zotero: null
summary: ai-draft
pdf: attachments/@hoeller2024anymal.pdf
status: to-read
mine: false
bibkeys:
- hoellerANYmalParkourLearning2024
---

# ANYmal Parkour: Learning Agile Navigation for Quadrupedal Robots

> [!info] David Hoeller; Nikita Rudin; Dhionis Sako; Marco Hutter · 2024 · Science Robotics

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A fully learned hierarchical pipeline lets a quadruped perform parkour-like agile navigation (walk/jump/climb/crouch) over challenging obstacles, transferred sim-to-real at up to 2 m/s.
**Problem** — Agile four-legged navigation is hard: highly dynamic motions, contacts across many parts of the robot, and a limited perception field of view.
**Method** — Train several advanced locomotion skills (walking, jumping, climbing, crouching), then a high-level policy selects and controls those skills across terrain. The hierarchical formulation makes the navigation policy aware of each skill's capabilities so it adapts behavior to the scenario. A perception module reconstructs obstacles from highly occluded, noisy sensory data for scene understanding.
**Key results** — Plans paths for challenging scenarios without expert demonstration, offline computation, prior environment knowledge, or explicit contact reasoning; trained purely in simulation with successful real-world transfer, crossing consecutive obstacles at speeds up to 2 m/s.

## Takeaways
- Skill-library + high-level selector where the selector is *capability-aware* of each low-level skill — a concrete capability-aware navigation architecture.
- Perception module reconstructs obstacle geometry from occluded/noisy input, decoupling scene understanding from control.
- No demonstrations, offline planning, or explicit contact modeling; pure sim training with zero-shot-style transfer.

## Relevance to your work
Directly on the capability-aware navigation line: a high-level policy that reasons about what each locomotion skill can do maps closely onto your interest in navigation that respects the locomotion layer's true capabilities. Hutter-group hierarchical + perceptive locomotion, transferable to humanoid parkour/navigation thinking on the G1.

## Abstract (from bib)
Performing agile navigation with four-legged robots is a challenging task because of the highly dynamic motions, contacts with various parts of the robot, and the limited field of view of the perception sensors. Here, we propose a fully learned approach to training such robots and conquer scenarios that are reminiscent of parkour challenges. The method involves training advanced locomotion skills for several types of obstacles, such as walking, jumping, climbing, and crouching, and then using a high-level policy to select and control those skills across the terrain. Thanks to our hierarchical formulation, the navigation policy is aware of the capabilities of each skill, and it will adapt its behavior depending on the scenario at hand. In addition, a perception module was trained to reconstruct obstacles from highly occluded and noisy sensory data and endows the pipeline with scene understanding. Compared with previous attempts, our method can plan a path for challenging scenarios without expert demonstration, offline computation, a priori knowledge of the environment, or taking contacts explicitly into account. Although these modules were trained from simulated data only, our real-world experiments demonstrate successful transfer on hardware, where the robot navigated and crossed consecutive challenging obstacles with speeds of up to 2 meters per second.

## Concepts
- [[capability-awareness]]
- [[hierarchical-control]]
- [[rl-for-legged-locomotion]]
- [[sim-to-real-transfer]]

## Source
- bibkeys: `hoellerANYmalParkourLearning2024`
- DOI: https://doi.org/10.1126/scirobotics.adi7566
- URL: https://www.science.org/doi/10.1126/scirobotics.adi7566
