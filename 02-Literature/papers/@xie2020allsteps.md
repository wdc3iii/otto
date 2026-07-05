---
type: paper
citekey: xie2020allsteps
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Xie, Zhaoming
- Ling, Hung Yu
- Kim, Nam Hee
- Panne, Michiel van de
year: 2020
venue: arXiv:2005.04323 [cs]
doi: 10.48550/arXiv.2005.04323
arxiv: '2005.04323'
url: https://arxiv.org/abs/2005.04323
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@xie2020allsteps.pdf
bibkeys:
- xie_allsteps_2020
---

# ALLSTEPS: Curriculum-driven Learning of Stepping Stone Skills

> [!info] Xie, Zhaoming; Ling, Hung Yu; Kim, Nam Hee; Panne, Michiel van de · 2020 · arXiv:2005.04323 [cs]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Fully learned RL controllers for stepping-stone locomotion with fully constrained footstep locations, showing that a learning curriculum is essential for efficient training.
**Problem** — Stepping-stone walking, where foot placements are fully constrained, is a longstanding hard problem in animation and robotics; naive RL learns it inefficiently.
**Method** — Train RL policies to hit constrained footstep targets and study the role of a curriculum: four curriculum choices are compared against a non-curriculum baseline across multiple embodiments.
**Key results** — A curriculum markedly improves learning efficiency; robust, plausible motions are produced for a simulated human character, a realistic bipedal robot, and a monster character across challenging stepping-stone sequences and terrains.

## Takeaways
- Curriculum design (how targets are sampled/progressed) is the decisive factor for learning fully-constrained foothold skills — the central empirical message.
- Demonstrates generality across embodiments, including a realistic bipedal robot, not just characters.
- An early, influential learned-foothold baseline that later sparse-foothold RL work (e.g. [[@wang2025beamdojo]]) builds on.

## Abstract (from bib)
Humans are highly adept at walking in environments with foot placement constraints, including stepping-stone scenarios where the footstep locations are fully constrained. Finding good solutions to stepping-stone locomotion is a longstanding and fundamental challenge for animation and robotics. We present fully learned solutions to this difficult problem using reinforcement learning. We demonstrate the importance of a curriculum for efficient learning and evaluate four possible curriculum choices compared to a non-curriculum baseline. Results are presented for a simulated human character, a realistic bipedal robot simulation and a monster character, in each case producing robust, plausible motions for challenging stepping stone sequences and terrains.

## Relevance to your work
A foundational demonstration that RL with the right curriculum can solve fully-constrained foothold locomotion — the learned-policy lineage behind foothold-aware walking in [[@dai2025walk]].

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `xie_allsteps_2020`
- arXiv: https://arxiv.org/abs/2005.04323
- DOI: https://doi.org/10.48550/arXiv.2005.04323
