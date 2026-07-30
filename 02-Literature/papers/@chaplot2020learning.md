---
type: paper
citekey: chaplot2020learning
tags: [navigation, planning]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Chaplot, Devendra Singh
- Gandhi, Dhiraj
- Gupta, Saurabh
- Gupta, Abhinav
- Salakhutdinov, Ruslan
year: 2020
venue: ICLR 2020
doi: 10.48550/arXiv.2004.05155
arxiv: '2004.05155'
url: https://arxiv.org/abs/2004.05155
pdf: attachments/@chaplot2020learning.pdf
zotero: null
status: to-read
mine: false
---

# Learning to Explore using Active Neural SLAM

> [!info] Devendra Singh Chaplot; Dhiraj Gandhi; Saurabh Gupta; Abhinav Gupta; Ruslan Salakhutdinov · 2020 · ICLR 2020
> arXiv:2004.05155 (2004.05155v1, 2020-04-10) · Published in ICLR-2020. See the project webpage at https://devendrachaplot.github.io/projects/Neural-SLAM for supplementary videos. The code is available at https://github.com/devendrachaplot/Neural-SLAM

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.2 (ref `[11]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[11]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Map / geometry / potential-field anticipation as supervised learning*. The canonical 'supervise the mapping module, RL only the policy' decomposition.

## Your take (your words — authoritative, not ai-draft)
> **Take:** the canonical "supervise the mapping module, RL only the policy" decomposition — the maximal version of what an aux head does partially.

## Abstract (from arXiv)
This work presents a modular and hierarchical approach to learn policies for exploring 3D
environments, called `Active Neural SLAM'. Our approach leverages the strengths of both classical
and learning-based methods, by using analytical path planners with learned SLAM module, and global
and local policies. The use of learning provides flexibility with respect to input modalities (in
the SLAM module), leverages structural regularities of the world (in global policies), and provides
robustness to errors in state estimation (in local policies). Such use of learning within each
module retains its benefits, while at the same time, hierarchical decomposition and modular training
allow us to sidestep the high sample complexities associated with training end-to-end policies. Our
experiments in visually and physically realistic simulated 3D environments demonstrate the
effectiveness of our approach over past learning and geometry-based approaches. The proposed model
can also be easily transferred to the PointGoal task and was the winning entry of the CVPR 2019
Habitat PointGoal Navigation Challenge.

## Concepts
- [[occupancy-anticipation]]
- [[mapless-navigation]]
- [[hierarchical-control]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/2004.05155 (2004.05155v1, published 2020-04-10, updated 2020-04-10)
- DOI: https://doi.org/10.48550/arXiv.2004.05155
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.2.
