---
type: paper
citekey: lambrechts2024informed
tags: [rl, method]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Lambrechts, Gaspard
- Bolland, Adrien
- Ernst, Damien
year: 2023
venue: RLC / RLJ 2024
doi: 10.48550/arXiv.2306.11488
arxiv: '2306.11488'
url: https://arxiv.org/abs/2306.11488
pdf: attachments/@lambrechts2024informed.pdf
zotero: null
status: to-read
mine: false
---

# Informed POMDP: Leveraging Additional Information in Model-Based RL

> [!info] Gaspard Lambrechts; Adrien Bolland; Damien Ernst · 2023 · RLC / RLJ 2024
> arXiv:2306.11488 (2306.11488v3, 2024-06-12) · In Reinforcement Learning Conference, 2024. 10 pages, 22 pages total, 10 figures

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.4 (ref `[20]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[20]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Memory, POMDPs, privileged information, and cautions*. **The theoretical licence for privileged aux targets.**

## Your take (your words — authoritative, not ai-draft)
> **Take:** the theoretical licence for privileged aux targets — the aux target may be privileged so long as the policy input is not.

## Abstract (from arXiv)
In this work, we generalize the problem of learning through interaction in a POMDP by accounting for
eventual additional information available at training time. First, we introduce the informed POMDP,
a new learning paradigm offering a clear distinction between the information at training and the
observation at execution. Next, we propose an objective that leverages this information for learning
a sufficient statistic of the history for the optimal control. We then adapt this informed objective
to learn a world model able to sample latent trajectories. Finally, we empirically show a learning
speed improvement in several environments using this informed world model in the Dreamer algorithm.
These results and the simplicity of the proposed adaptation advocate for a systematic consideration
of eventual additional information when learning in a POMDP using model-based RL.

## Concepts
- [[privileged-information]]
- [[belief-state]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/2306.11488 (2306.11488v3, published 2023-06-20, updated 2024-06-12)
- DOI: https://doi.org/10.48550/arXiv.2306.11488
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.4.
