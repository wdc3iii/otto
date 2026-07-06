---
type: paper
citekey: rudin2021learning
tags: [rl, locomotion]
aliases: []
created: '2026-07-05'
modified: '2026-07-06'
authors:
- Nikita Rudin
- David Hoeller
- Philipp Reist
- Marco Hutter
year: 2021
venue: 'Conference on Robot Learning (CoRL 2021 / PMLR)'
doi: null
arxiv: 2109.11978
url: https://arxiv.org/abs/2109.11978
pdf: attachments/@rudin2021learning.pdf
zotero: null
status: to-read
summary: ai-draft
mine: false
bibkeys:
- Rudin2021
- rudinLearningWalkMinutes2022
---

# Learning to Walk in Minutes Using Massively Parallel Deep Reinforcement Learning

> [!info] Nikita Rudin; David Hoeller; Philipp Reist; Marco Hutter · 2021 · Conference on Robot Learning (CoRL)
> [!info]- otto authors: [[marco-hutter]]

> [!note] AI-drafted from the arXiv abstract (not full text) — a base to edit. Flip `summary: ai-draft` → `reviewed` once you've checked it.

## Summary
**TL;DR** — Trains legged-locomotion RL policies with **thousands of robots in parallel on a single GPU** plus a game-inspired terrain curriculum, cutting training from hours/days to **minutes**; validated on ANYmal in sim and on hardware.
**Problem** — RL for legged locomotion is slow to train; the goal is fast policy generation on commodity (single-workstation) hardware.
**Method** — Massively parallel simulation on one GPU; analysis of which training-algorithm components matter in the massively-parallel regime; a novel game-inspired curriculum suited to thousands of parallel robots.
**Key results** — Flat-terrain policy in **< 4 min**, uneven terrain in **~20 min** (orders-of-magnitude speedup); successful sim-to-real transfer to ANYmal; training code open-sourced.

## Takeaways
- Established the now-standard "**thousands of envs on one GPU**" recipe (Isaac Gym) for legged RL.
- **Curriculum design** matters as much as raw parallelism for final performance.
- The speedup is what makes data-hungry downstream methods (learned tubes, distillation) practical.

## Relevance to your work
The massively-parallel-simulation foundation your [[@compton2025dynamic|DTMPC]] relies on to collect 400k+ trajectories for learning tube dynamics, and the backbone of your RL-locomotion line ([[@csomayshanklin2024robust]] and the terrain/running papers). Cited as the parallel-RL precedent (ref [25]).

## Concepts
- [[massively-parallel-simulation]]

## Source
- arXiv: https://arxiv.org/abs/2109.11978 · PDF: `attachments/@rudin2021learning.pdf`
- Cited by [[@compton2025dynamic]]
- bibkeys: `Rudin2021`
