---
type: paper
citekey: pasukonis2022evaluating
tags: [rl, open-question]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Pasukonis, Jurgis
- Lillicrap, Timothy
- Hafner, Danijar
year: 2022
venue: arXiv preprint (Memory Maze)
doi: 10.48550/arXiv.2210.13383
arxiv: '2210.13383'
url: https://arxiv.org/abs/2210.13383
pdf: attachments/@pasukonis2022evaluating.pdf
zotero: null
status: to-read
mine: false
---

# Evaluating Long-Term Memory in 3D Mazes

> [!info] Jurgis Pasukonis; Timothy Lillicrap; Danijar Hafner · 2022 · arXiv preprint (Memory Maze)
> arXiv:2210.13383 (2210.13383v1, 2022-10-24) · Project website: https://github.com/jurgisp/memory-maze

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.4 (ref `[19]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[19]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Memory, POMDPs, privileged information, and cautions*. **Evidence that reward alone under-trains memory** — the general case for supervising it.

## Your take (your words — authoritative, not ai-draft)
> **Take:** evidence that reward alone under-trains memory — the general argument for supervising it — and a probing methodology close to our `gradient_diagnostic` harness.

## Abstract (from arXiv)
Intelligent agents need to remember salient information to reason in partially-observed
environments. For example, agents with a first-person view should remember the positions of relevant
objects even if they go out of view. Similarly, to effectively navigate through rooms agents need to
remember the floor plan of how rooms are connected. However, most benchmark tasks in reinforcement
learning do not test long-term memory in agents, slowing down progress in this important research
direction. In this paper, we introduce the Memory Maze, a 3D domain of randomized mazes specifically
designed for evaluating long-term memory in agents. Unlike existing benchmarks, Memory Maze measures
long-term memory separate from confounding agent abilities and requires the agent to localize itself
by integrating information over time. With Memory Maze, we propose an online reinforcement learning
benchmark, a diverse offline dataset, and an offline probing evaluation. Recording a human player
establishes a strong baseline and verifies the need to build up and retain memories, which is
reflected in their gradually increasing rewards within each episode. We find that current algorithms
benefit from training with truncated backpropagation through time and succeed on small mazes, but
fall short of human performance on the large mazes, leaving room for future algorithmic designs to
be evaluated on the Memory Maze.

## Concepts
- [[belief-state]]
- [[auxiliary-task-learning]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/2210.13383 (2210.13383v1, published 2022-10-24, updated 2022-10-24)
- DOI: https://doi.org/10.48550/arXiv.2210.13383
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.4.
