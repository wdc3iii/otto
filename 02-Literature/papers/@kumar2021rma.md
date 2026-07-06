---
type: paper
citekey: kumar2021rma
tags: [locomotion, rl, control]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Kumar, Ashish
- Fu, Zipeng
- Pathak, Deepak
- Malik, Jitendra
year: 2021
venue: arXiv
doi: 10.48550/arXiv.2107.04034
arxiv: '2107.04034'
url: http://arxiv.org/abs/2107.04034
zotero: null
summary: ai-draft
pdf: attachments/@kumar2021rma.pdf
status: to-read
mine: false
bibkeys:
- kumarRMARapidMotor2021
---

# RMA: Rapid Motor Adaptation for Legged Robots

> [!info] Ashish Kumar; Zipeng Fu; Deepak Pathak; Jitendra Malik · 2021 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — RMA pairs a base RL policy with an adaptation module that infers environment properties from recent state-action history, enabling sub-second real-time adaptation to novel terrains and disturbances, trained purely in sim and deployed zero-shot on A1.
**Problem** — Real-world legged deployment demands real-time adaptation to unseen conditions — changing terrain, payloads, wear and tear.
**Method** — Two components: a base policy and an adaptation module; together they let the robot adapt to novel situations in fractions of a second. Trained entirely in simulation without domain knowledge (no reference trajectories or predefined foot trajectory generators), using a varied terrain generator and bioenergetics-inspired rewards; deployed on A1 without fine-tuning.
**Key results** — State-of-the-art performance across diverse real-world and simulation experiments; deployed on rocky, slippery, deformable surfaces with grass, long vegetation, concrete, pebbles, stairs, sand (no numeric figures read).

## Takeaways
- Adaptation module estimates a latent extrinsics vector online from history, decoupling "what environment am I in" from "how do I act."
- Fully sim-trained with no reference motions or trajectory generators; zero-shot to hardware.
- Bioenergetics-inspired reward shapes natural, efficient gaits without hand-designed primitives.

## Relevance to your work
RMA is a foundational RL-locomotion adaptation method squarely in your wheelhouse: the teacher/adaptation-module structure and sim-to-real story inform how you'd give a G1 humanoid policy fast online adaptation to terrain and payload changes.

## Abstract (from bib)
Successful real-world deployment of legged robots would require them to adapt in real-time to unseen scenarios like changing terrains, changing payloads, wear and tear. This paper presents Rapid Motor Adaptation (RMA) algorithm to solve this problem of real-time online adaptation in quadruped robots. RMA consists of two components: a base policy and an adaptation module. The combination of these components enables the robot to adapt to novel situations in fractions of a second. RMA is trained completely in simulation without using any domain knowledge like reference trajectories or predefined foot trajectory generators and is deployed on the A1 robot without any fine-tuning. We train RMA on a varied terrain generator using bioenergetics-inspired rewards and deploy it on a variety of difficult terrains including rocky, slippery, deformable surfaces in environments with grass, long vegetation, concrete, pebbles, stairs, sand, etc. RMA shows state-of-the-art performance across diverse real-world as well as simulation experiments. Video results at https://ashish-kmr.github.io/rma-legged-robots/

## Concepts
- [[rl-for-legged-locomotion]]
- [[sim-to-real-transfer]]

## Source
- bibkeys: `kumarRMARapidMotor2021`
- arXiv: http://arxiv.org/abs/2107.04034
- DOI: https://doi.org/10.48550/arXiv.2107.04034
- URL: http://arxiv.org/abs/2107.04034
