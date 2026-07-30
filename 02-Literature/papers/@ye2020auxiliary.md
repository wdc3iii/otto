---
type: paper
citekey: ye2020auxiliary
tags: [rl, navigation]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Ye, Joel
- Batra, Dhruv
- Wijmans, Erik
- Das, Abhishek
year: 2020
venue: CoRL 2020 (PMLR v155)
doi: 10.48550/arXiv.2007.04561
arxiv: '2007.04561'
url: https://arxiv.org/abs/2007.04561
pdf: attachments/@ye2020auxiliary.pdf
zotero: null
status: to-read
mine: false
---

# Auxiliary Tasks Speed Up Learning PointGoal Navigation

> [!info] Joel Ye; Dhruv Batra; Erik Wijmans; Abhishek Das · 2020 · CoRL 2020 (PMLR v155)
> arXiv:2007.04561 (2007.04561v2, 2020-11-04) · 8 pages. Accepted to CoRL 2020

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.1 (ref `[3]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[3]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Auxiliary tasks in navigation RL*. **The practical recipe to copy**: loss weighting and subsampling.

## Your take (your words — authoritative, not ai-draft)
> **Take:** the loss-weighting rule and the subsampling trick, both directly portable.

## Abstract (from arXiv)
PointGoal Navigation is an embodied task that requires agents to navigate to a specified point in an
unseen environment. Wijmans et al. showed that this task is solvable but their method is
computationally prohibitive, requiring 2.5 billion frames and 180 GPU-days. In this work, we develop
a method to significantly increase sample and time efficiency in learning PointNav using
self-supervised auxiliary tasks (e.g. predicting the action taken between two egocentric
observations, predicting the distance between two observations from a trajectory,etc.).We find that
naively combining multiple auxiliary tasks improves sample efficiency,but only provides marginal
gains beyond a point. To overcome this, we use attention to combine representations learnt from
individual auxiliary tasks. Our best agent is 5.5x faster to reach the performance of the previous
state-of-the-art, DD-PPO, at 40M frames, and improves on DD-PPO's performance at 40M frames by 0.16
SPL. Our code is publicly available at https://github.com/joel99/habitat-pointnav-aux.

## Concepts
- [[auxiliary-task-learning]]
- [[recurrent-navigation-policy]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/2007.04561 (2007.04561v2, published 2020-07-09, updated 2020-11-04)
- DOI: https://doi.org/10.48550/arXiv.2007.04561
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.1.
