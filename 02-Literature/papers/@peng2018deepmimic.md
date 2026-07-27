---
type: paper
citekey: peng2018deepmimic
tags: [rl]
aliases: []
created: '2026-07-26'
modified: '2026-07-26'
authors:
- Peng, Xue Bin
- Abbeel, Pieter
- Levine, Sergey
- van de Panne, Michiel
year: 2018
venue: SIGGRAPH
doi: 10.48550/arXiv.1804.02717
arxiv: '1804.02717'
url: https://arxiv.org/abs/1804.02717
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@peng2018deepmimic.pdf
---

# DeepMimic: Example-Guided Deep Reinforcement Learning of Physics-Based Character Skills

> [!info] Peng, Xue Bin; Abbeel, Pieter; Levine, Sergey; van de Panne, Michiel · 2018 · SIGGRAPH

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — Adapts standard deep RL to imitate individual reference motion clips in physics-based simulation, producing robust, natural control policies that track a broad range of example motions — from keyframed and mocap flips/spins to retargeted clips — while also satisfying user-specified task goals.

**Problem** — A longstanding animation goal is to combine data-driven specification of behavior with a controller that reproduces similar behavior in physical simulation, so it responds realistically to perturbations and environmental variation. The gap: how to get the motion quality and convenience of reference clips together with the flexibility and generality of RL + physics-based animation.

**Method** — Combine a motion-imitation objective (track a reference clip) with a task objective (e.g. walk in a desired direction, throw a ball at a target), training control policies with well-known RL methods. The paper further explores several methods for integrating multiple clips into learning to build multi-skilled agents. (inferred) The imitation objective is a per-frame reward comparing the policy's state to the reference motion, which is what lets a single RL setup span diverse clips.

**Key results** — Learns robust policies that imitate a broad range of clips while also learning complex recoveries, adapting to changes in morphology, and accomplishing user-specified goals. Handles keyframed motions, highly dynamic mocap actions (flips, spins), and retargeted motions. Demonstrated across multiple characters (human, Atlas robot, bipedal dinosaur, dragon) and a large variety of skills spanning locomotion, acrobatics, and martial arts. (No quantitative benchmarks stated in the abstract.)

**Limitations / open questions** — (inferred) Not discussed in the abstract; each skill is defined by a reference clip, so coverage and composition of skills depend on the available motion data and the multi-clip integration schemes explored here — a limitation that later work (AMP/ASE, BeyondMimic) targets directly.

## Concepts

[[motion-imitation]], [[rl-for-legged-locomotion]]

> proposed links.

## Relevance to your work
DeepMimic is the ancestor of the reference-motion-tracking + RL lineage that runs through AMP/ASE to [[@liao2025beyondmimic]]; the imitation-plus-task-objective recipe here is the foundation for the humanoid whole-body skill learning you're pursuing on the Unitree G1.

## Abstract (from arXiv)
A longstanding goal in character animation is to combine data-driven specification of behavior with a system that can execute a similar behavior in a physical simulation, thus enabling realistic responses to perturbations and environmental variation. We show that well-known reinforcement learning (RL) methods can be adapted to learn robust control policies capable of imitating a broad range of example motion clips, while also learning complex recoveries, adapting to changes in morphology, and accomplishing user-specified goals. Our method handles keyframed motions, highly-dynamic actions such as motion-captured flips and spins, and retargeted motions. By combining a motion-imitation objective with a task objective, we can train characters that react intelligently in interactive settings, e.g., by walking in a desired direction or throwing a ball at a user-specified target. This approach thus combines the convenience and motion quality of using motion clips to define the desired style and appearance, with the flexibility and generality afforded by RL methods and physics-based animation. We further explore a number of methods for integrating multiple clips into the learning process to develop multi-skilled agents capable of performing a rich repertoire of diverse skills. We demonstrate results using multiple characters (human, Atlas robot, bipedal dinosaur, dragon) and a large variety of skills, including locomotion, acrobatics, and martial arts.

## Source
- arXiv: https://arxiv.org/abs/1804.02717
- PDF: https://arxiv.org/pdf/1804.02717
- DOI: https://doi.org/10.48550/arXiv.1804.02717
