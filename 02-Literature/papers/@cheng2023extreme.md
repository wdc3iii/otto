---
type: paper
citekey: cheng2023extreme
tags: [locomotion, rl]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Cheng, Xuxin
- Shi, Kexin
- Agarwal, Ananye
- Pathak, Deepak
year: 2023
venue: arXiv
doi: 10.48550/arXiv.2309.14341
arxiv: '2309.14341'
url: http://arxiv.org/abs/2309.14341
zotero: null
summary: ai-draft
pdf: attachments/@cheng2023extreme.pdf
status: to-read
mine: false
bibkeys:
- chengExtremeParkourLegged2023
---

# Extreme Parkour with Legged Robots

> [!info] Xuxin Cheng; Kexin Shi; Ananye Agarwal; Deepak Pathak · 2023 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A single neural-net policy operating directly on depth-camera images, trained in simulation with large-scale RL, produces highly precise parkour behaviors on a low-cost legged robot despite imprecise sensing and actuation.
**Problem** — Classical parkour pipelines engineer perception, actuation, and control to very low tolerances, restricting robots to tightly controlled predetermined obstacle courses; humans instead learn parkour through practice.
**Method** — Train one end-to-end policy from a single front-facing depth camera (low-frequency, jittery, artifact-prone) with large-scale RL in simulation, so the network learns to output precise control despite imprecise sensing/actuation.
**Key results** — On a small low-cost robot: high jump onto obstacles 2x its height, long jump across gaps 2x its length, handstand, running across tilted ramps, and generalization to novel obstacle courses with different physical properties. (no other numeric figures read)

## Takeaways
- End-to-end depth-image-to-control policy replaces the engineered perception→planning→control stack for agile, discrete-contact maneuvers.
- Large-scale simulation RL compensates for cheap, jittery hardware — precision emerges from the policy, not the sensor/actuator tolerances.
- Demonstrates generalization to unseen obstacle courses, a step beyond fixed-course parkour.

## Relevance to your work
A high-water-mark for RL perceptive locomotion and a natural benchmark/contrast for agility on the G1: it argues extreme dynamic maneuvers can be learned end-to-end, versus your CLF/CBF + reduced-order-model approach to guaranteeing feasibility.

## Abstract (from bib)
Humans can perform parkour by traversing obstacles in a highly dynamic fashion requiring precise eye-muscle coordination and movement. Getting robots to do the same task requires overcoming similar challenges. Classically, this is done by independently engineering perception, actuation, and control systems to very low tolerances. This restricts them to tightly controlled settings such as a predetermined obstacle course in labs. In contrast, humans are able to learn parkour through practice without significantly changing their underlying biology. In this paper, we take a similar approach to developing robot parkour on a small low-cost robot with imprecise actuation and a single front-facing depth camera for perception which is low-frequency, jittery, and prone to artifacts. We show how a single neural net policy operating directly from a camera image, trained in simulation with large-scale RL, can overcome imprecise sensing and actuation to output highly precise control behavior end-to-end. We show our robot can perform a high jump on obstacles 2x its height, long jump across gaps 2x its length, do a handstand and run across tilted ramps, and generalize to novel obstacle courses with different physical properties. Parkour videos at https://extreme-parkour.github.io/

## Concepts
- [[rl-for-legged-locomotion]]
- [[sim-to-real-transfer]]

## Source
- bibkeys: `chengExtremeParkourLegged2023`
- arXiv: http://arxiv.org/abs/2309.14341
- DOI: https://doi.org/10.48550/arXiv.2309.14341
- URL: http://arxiv.org/abs/2309.14341
