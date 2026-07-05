---
type: paper
citekey: sleiman2026zest
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Sleiman, Jean Pierre
- Li, He
- Adu-Bredu, Alphonsus
- Deits, Robin
- Kumar, Arun
- others
year: 2026
venue: arXiv
doi: 10.48550/arXiv.2602.00401
arxiv: '2602.00401'
url: https://arxiv.org/abs/2602.00401
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@sleiman2026zest.pdf
bibkeys:
- sleiman2026zest
- sleiman_zest_2026
---

# ZEST: Zero-shot Embodied Skill Transfer for Athletic Robot Control

> [!info] Sleiman, Jean Pierre; Li, He; Adu-Bredu, Alphonsus; Deits, Robin; Kumar, Arun; others · 2026 · arXiv

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — ZEST is a streamlined motion-imitation framework that trains RL policies from heterogeneous sources (mocap, monocular video, non-physical animation) and deploys them zero-shot to hardware across multiple robot morphologies.
**Problem** — Robust, human-like whole-body control for agile, contact-rich humanoid behaviors demands heavy per-skill engineering and brittle controller tuning.
**Method** — ZEST learns policies via RL from diverse demonstration sources while avoiding contact labels, reference/observation windows, state estimators, and extensive reward shaping. Its pipeline combines adaptive sampling (focusing on hard motion segments) with an automatic curriculum using a model-based assistive wrench for dynamic long-horizon maneuvers, plus a procedure to pick joint gains from approximate analytical armature values and a refined actuator model. Training is entirely in simulation with moderate domain randomization.
**Key results** — On Atlas it learns multi-contact skills (army crawl, breakdancing) from mocap and transfers dance and box-climbing from video; skills transfer to the Unitree G1 and, across morphologies, to the Spot quadruped (continuous backflip from animation) — all zero-shot to hardware.

## Takeaways
- Ingests wildly different demonstration modalities (mocap, video, animation) into one imitation pipeline without contact labels or state estimators.
- Adaptive sampling + a model-based assistive-wrench curriculum are the levers for dynamic, long-horizon skills.
- Zero-shot cross-embodiment transfer (Atlas, G1, Spot) from sim with only moderate domain randomization is the headline generality claim.

## Abstract (from bib)
Achieving robust, human-like whole-body control on humanoid robots for agile, contact-rich behaviors remains a central challenge, demanding heavy per-skill engineering and a brittle process of tuning controllers. We introduce ZEST (Zero-shot Embodied Skill Transfer), a streamlined motion-imitation framework that trains policies via reinforcement learning from diverse sources -- high-fidelity motion capture, noisy monocular video, and non-physics-constrained animation -- and deploys them to hardware zero-shot. ZEST generalizes across behaviors and platforms while avoiding contact labels, reference or observation windows, state estimators, and extensive reward shaping. Its training pipeline combines adaptive sampling, which focuses training on difficult motion segments, and an automatic curr

## Concepts


## Relevance to your work
A recent benchmark for learned, cross-embodiment agile control (including the Unitree G1): its heavy-imitation, minimal-structure recipe is a useful contrast to stability-certified, model-grounded approaches like [[@olkin2026chasing]].

## Source
- Cited by [[@olkin2026stability]], [[@terrain2026consistent]]
- bibkeys: `sleiman2026zest`, `sleiman_zest_2026`
- arXiv: https://arxiv.org/abs/2602.00401
- DOI: https://doi.org/10.48550/arXiv.2602.00401
