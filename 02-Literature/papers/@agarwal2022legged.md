---
type: paper
citekey: agarwal2022legged
tags: [locomotion, rl]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Agarwal, Ananye
- Kumar, Ashish
- Malik, Jitendra
- Pathak, Deepak
year: 2022
venue: arXiv
doi: 10.48550/arXiv.2211.07638
arxiv: '2211.07638'
url: http://arxiv.org/abs/2211.07638
zotero: null
summary: ai-draft
pdf: attachments/@agarwal2022legged.pdf
status: to-read
mine: false
bibkeys:
- agarwalLeggedLocomotionChallenging2022
---

# Legged Locomotion in Challenging Terrains Using Egocentric Vision

> [!info] Ananye Agarwal; Ashish Kumar; Jitendra Malik; Deepak Pathak · 2022 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — An end-to-end RL locomotion policy driven by a single front-facing depth camera lets a small quadruped traverse stairs, curbs, stepping stones, and gaps without explicit elevation mapping.
**Problem** — Traditional pipelines decompose vision-based locomotion into elevation mapping + foothold planning; the mapping stage is noise-prone, needs specialized hardware, and is biologically implausible.
**Method** — Train in simulation in two phases: (1) RL with a cheap-to-compute proxy for the depth image, then (2) supervised distillation into a policy that consumes real depth. The egocentric camera forces the policy to remember past observations to estimate terrain under the hind feet; the small robot required discovering specialized gaits.
**Key results** — Transfers to the real world and runs in real time on the robot's limited compute; traverses varied terrain and is robust to pushes, slippery surfaces, and rocky ground. (no numeric figures read)

## Takeaways
- End-to-end depth-to-action policy sidesteps the fragile elevation-mapping stage entirely.
- Two-phase recipe: RL with a cheap depth proxy, then supervised distillation to real depth — a recurring pattern for making perceptive policies deployable.
- Memory in the policy is essential because the forward-facing camera cannot see the terrain under the hind feet at contact time.

## Relevance to your work
Directly on your perceptive/terrain-aware locomotion line: an existence proof that a single depth camera + RL, with no elevation map, handles discrete-contact terrain — a design point to contrast against your CLF/CBF + reduced-order model planning on the G1.

## Abstract (from bib)
Animals are capable of precise and agile locomotion using vision. Replicating this ability has been a long-standing goal in robotics. The traditional approach has been to decompose this problem into elevation mapping and foothold planning phases. The elevation mapping, however, is susceptible to failure and large noise artifacts, requires specialized hardware, and is biologically implausible. In this paper, we present the first end-to-end locomotion system capable of traversing stairs, curbs, stepping stones, and gaps. We show this result on a medium-sized quadruped robot using a single front-facing depth camera. The small size of the robot necessitates discovering specialized gait patterns not seen elsewhere. The egocentric camera requires the policy to remember past information to estimate the terrain under its hind feet. We train our policy in simulation. Training has two phases - first, we train a policy using reinforcement learning with a cheap-to-compute variant of depth image and then in phase 2 distill it into the final policy that uses depth using supervised learning. The resulting policy transfers to the real world and is able to run in real-time on the limited compute of the robot. It can traverse a large variety of terrain while being robust to perturbations like pushes, slippery surfaces, and rocky terrain. Videos are at https://vision-locomotion.github.io

## Concepts
- [[rl-for-legged-locomotion]]
- [[sim-to-real-transfer]]

## Source
- bibkeys: `agarwalLeggedLocomotionChallenging2022`
- arXiv: http://arxiv.org/abs/2211.07638
- DOI: https://doi.org/10.48550/arXiv.2211.07638
- URL: http://arxiv.org/abs/2211.07638
