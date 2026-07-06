---
type: paper
citekey: lee2020quadrupedal
tags: [locomotion, rl, control]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Lee, Joonho
- Hwangbo, Jemin
- Wellhausen, Lorenz
- Koltun, Vladlen
- Hutter, Marco
year: 2020
venue: Science Robotics
doi: 10.1126/scirobotics.abc5986
arxiv: '2010.11251'
url: http://arxiv.org/abs/2010.11251
zotero: null
summary: ai-draft
pdf: attachments/@lee2020quadrupedal.pdf
status: to-read
mine: false
bibkeys:
- leeLearningQuadrupedalLocomotion2020
---

# Learning Quadrupedal Locomotion over Challenging Terrain

> [!info] Joonho Lee; Jemin Hwangbo; Lorenz Wellhausen; Vladlen Koltun; Marco Hutter · 2020 · Science Robotics

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A purely proprioceptive RL controller, trained in simulation, gives ANYmal radically robust zero-shot locomotion across mud, snow, rubble, vegetation, and running water — beyond prior published legged work.
**Problem** — Conventional legged controllers rely on elaborate state machines triggering motion primitives/reflexes; they grow in complexity yet fall short of animal-level generality and robustness in challenging natural environments.
**Method** — A neural network controller acting on a stream of proprioceptive signals, trained by reinforcement learning in simulation, with a novel way to incorporate proprioceptive feedback into locomotion control.
**Key results** — Remarkable zero-shot sim-to-real generalization; robust under conditions never seen in training — deformable terrain (mud, snow), dynamic footholds (rubble), overground impediments (thick vegetation, gushing water) — across two generations of ANYmal (no numeric figures read).

## Takeaways
- Proprioception-only control (no exteroception) can be strikingly robust — argues radical robustness is achievable by training in much simpler simulated domains.
- Uses a teacher-student / privileged-learning-style pipeline to distill a deployable proprioceptive policy (a landmark for the approach).
- Zero-shot transfer to natural terrains defines a robustness benchmark for later perceptive-locomotion work.

## Relevance to your work
A seminal RL-locomotion + sim-to-real paper directly on your line; the proprioceptive-robustness result is the baseline that perceptive/terrain-aware methods build on, and the privileged-learning structure informs your G1 policy design.

## Abstract (from bib)
Some of the most challenging environments on our planet are accessible to quadrupedal animals but remain out of reach for autonomous machines. Legged locomotion can dramatically expand the operational domains of robotics. However, conventional controllers for legged locomotion are based on elaborate state machines that explicitly trigger the execution of motion primitives and reflexes. These designs have escalated in complexity while falling short of the generality and robustness of animal locomotion. Here we present a radically robust controller for legged locomotion in challenging natural environments. We present a novel solution to incorporating proprioceptive feedback in locomotion control and demonstrate remarkable zero-shot generalization from simulation to natural environments. The controller is trained by reinforcement learning in simulation. It is based on a neural network that acts on a stream of proprioceptive signals. The trained controller has taken two generations of quadrupedal ANYmal robots to a variety of natural environments that are beyond the reach of prior published work in legged locomotion. The controller retains its robustness under conditions that have never been encountered during training: deformable terrain such as mud and snow, dynamic footholds such as rubble, and overground impediments such as thick vegetation and gushing water. The presented work opens new frontiers for robotics and indicates that radical robustness in natural environments can be achieved by training in much simpler domains.

## Concepts
- [[rl-for-legged-locomotion]]
- [[sim-to-real-transfer]]

## Source
- bibkeys: `leeLearningQuadrupedalLocomotion2020`
- arXiv: http://arxiv.org/abs/2010.11251
- DOI: https://doi.org/10.1126/scirobotics.abc5986
- URL: http://arxiv.org/abs/2010.11251
