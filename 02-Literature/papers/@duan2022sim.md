---
type: paper
citekey: duan2022sim
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Duan, Helei
- Malik, Ashish
- Dao, Jeremy
- Saxena, Aseem
- Green, Kevin
- Siekmann, Jonah
- Fern, Alan
- Hurst, Jonathan
year: 2022
venue: null
doi: 10.1109/ICRA46639.2022.9812015
arxiv: 2203.07589
url: https://arxiv.org/abs/2203.07589
zotero: null
summary: ai-draft
pdf: attachments/@duan2022sim.pdf
status: to-read
mine: false
bibkeys:
- duan_sim--real_2022
---

# Sim-to-Real Learning of Footstep-Constrained Bipedal Dynamic Walking

> [!info] Duan, Helei; Malik, Ashish; Dao, Jeremy; Saxena, Aseem; Green, Kevin; Siekmann, Jonah · 2022 · —

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — An RL formulation that lets a dynamic bipedal gait controller respond to externally specified touchdown locations, keeping robust learned gaits while respecting footstep constraints, demonstrated sim-to-real on Cassie.
**Problem** — RL bipedal controllers achieve robust dynamic gaits by taking full freedom over foot placement, but the real world imposes feasible-footstep constraints (from perception). Most RL controllers lack the interface to specify and respond to such constraints, limiting real-world use.
**Method** — Trains, via RL, a dynamic gait controller conditioned on specified touchdown locations so it tracks commanded footsteps while staying balanced. Separately uses supervised learning to induce a transition model that predicts, from proprioceptive observations, the next touchdown locations the controller can actually achieve — enabling integration into a full-order locomotion planner.
**Key results** — Demonstrates both simulation and sim-to-real performance on Cassie; the learned transition model accurately predicts achievable touchdowns (no numeric metrics seen in the abstract).

## Takeaways
- Adds a footstep-command interface to robust RL gaits — the missing control handle for perception-constrained walking.
- The learned proprioceptive transition model (achievable next footholds) is what bridges the controller to a higher-level planner.
- Companion/precursor to the stepping-stones work; here the emphasis is the constraint interface and sim-to-real, not perception.

## Relevance to your work
Establishes the footstep-conditioned RL controller plus achievability model that later stepping-stone systems build on; cited by [[@dai2025walk]] as prior art on footstep-constrained bipedal walking.

## Abstract (from bib)
Recently, work on reinforcement learning (RL) for bipedal robots has successfully learned controllers for a variety of dynamic gaits with robust sim-to-real demonstrations. In order to maintain balance, the learned controllers have full freedom of where to place the feet, resulting in highly robust gaits. In the real world however, the environment will often impose constraints on the feasible footstep locations, typically identiﬁed by perception systems. Unfortunately, most demonstrated RL controllers on bipedal robots do not allow for specifying and responding to such constraints. This missing control interface greatly limits the real-world application of current RL controllers. In this paper, we aim to maintain the robust and dynamic nature of learned gaits while also respecting footstep

## Concepts

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `duan_sim--real_2022`
