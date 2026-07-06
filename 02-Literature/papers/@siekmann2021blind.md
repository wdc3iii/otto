---
type: paper
citekey: siekmann2021blind
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-06'
authors:
- Siekmann, Jonah
- Green, Kevin
- Warila, John
- Fern, Alan
- Hurst, Jonathan
year: 2021
venue: arXiv preprint arXiv:2105.08328
doi: null
arxiv: '2105.08328'
url: https://arxiv.org/abs/2105.08328
zotero: null
summary: ai-draft
pdf: attachments/@siekmann2021blind.pdf
status: to-read
mine: false
bibkeys:
- siekmann2021blind
- siekmannBlindBipedalStair2021
---

# Blind bipedal stair traversal via sim-to-real reinforcement learning

> [!info] Siekmann, Jonah; Green, Kevin; Warila, John; Fern, Alan; Hurst, Jonathan · 2021 · arXiv preprint arXiv:2105.08328

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Sim-to-real RL yields a blind, proprioception-only bipedal controller that reliably traverses real-world stairs on Cassie.
**Problem** — Accurate terrain estimation is hard and brittle in the real world; the paper asks how far locomotion can get with no external perception or terrain model at all.
**Method** — Trains an RL locomotion policy in simulation using only proprioceptive feedback, then transfers to hardware. The key move is minimal: take an existing flat-terrain RL training framework and add stair-like terrain randomization during training — with no change to the reward function.
**Key results** — Produces the first controller for a bipedal, human-scale robot (Cassie) that reliably traverses a variety of real-world stairs and stair-like disturbances using proprioception alone. (Accepted to RSS 2021.)

## Takeaways
- Terrain randomization in sim, not perception, is enough to get robust blind stair traversal — a strong argument for proprioceptive robustness over fragile terrain estimation.
- No reward-function redesign was needed; the gain came purely from the training distribution.
- Blind by construction — no vision/elevation map — which is the point but also the ceiling on what it can anticipate.

## Relevance to your work
A reference point for proprioception-only, sim-to-real RL locomotion on real bipedal hardware — the learning-based counterpart to model-based terrain handling, relevant to work like [[@dai2025walk]].

## Concepts


## Source
- Cited by [[@compton2024constructive]]
- bibkeys: `siekmann2021blind`
- arXiv: https://arxiv.org/abs/2105.08328
