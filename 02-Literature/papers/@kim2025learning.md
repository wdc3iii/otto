---
type: paper
citekey: kim2025learning
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Kim, Minku
- Acosta, Brian
- Chaudhari, Pratik
- Posa, Michael
year: 2025
venue: 2025 IEEE-RAS 24th International Conference on Humanoid Robots (Humanoids)
doi: 10.1109/Humanoids65713.2025.11203087
arxiv: null
url: https://doi.org/10.1109/Humanoids65713.2025.11203087
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- kim_learning_2025
---

# Learning a Vision-Based Footstep Planner for Hierarchical Walking Control

> [!info] Kim, Minku; Acosta, Brian; Chaudhari, Pratik; Posa, Michael · 2025 · 2025 IEEE-RAS 24th International Conference on Humanoid Robots (Humanoids)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A vision-based hierarchical walking controller pairing an RL high-level footstep planner (fed a local elevation map) with a low-level Operational Space Controller that tracks the planned trajectories.
**Problem** — Bipedal locomotion frameworks that rely on proprioception alone or hand-designed vision pipelines are fragile in real, unstructured terrain and make real-time footstep planning hard.
**Method** — A reinforcement-learning high-level planner generates footstep commands from a local elevation map; a low-level OSC tracks them. The state is compressed via the Angular Momentum Linear Inverted Pendulum (AM-LIP) model to give a low-dimensional, dynamically informative representation while cutting complexity.
**Key results** — Evaluated across terrain conditions on the underactuated biped Cassie in both simulation and hardware, examining the capabilities and challenges of the approach.

## Takeaways
- The AM-LIP reduced-order model is the interface between the learned planner and the model-based tracker, keeping the RL problem low-dimensional.
- Learning the footstep planner (rather than the full policy) while keeping a model-based OSC below is a clean hierarchical split.
- Uses perceptive input (elevation map) directly, avoiding brittle hand-tuned vision pipelines.

## Relevance to your work
A concrete hierarchical, reduced-order-mediated split of learned high-level footstep planning over model-based low-level tracking — the same architecture family as [[@dai2025walk]], and a direct point of comparison on how the planner/controller interface is structured.

## Abstract (from bib)
Bipedal robots demonstrate potential in navigating challenging terrains through dynamic ground contact. However, current frameworks often depend solely on proprioception or use manually designed visual pipelines, which are fragile in real-world settings and complicate real-time footstep planning in unstructured environments. To address this problem, we present a vision-based hierarchical control framework that integrates a reinforcement learning high-level footstep planner, which generates footstep commands based on a local elevation map, with a low-level Operational Space Controller that tracks the generated trajectories. We utilize the Angular Momentum Linear Inverted Pendulum model to construct a low-dimensional state representation to capture an informative encoding of the dynamics whi

## Concepts
[[hierarchical-control]], [[reduced-order-model]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `kim_learning_2025`
- DOI: https://doi.org/10.1109/Humanoids65713.2025.11203087
