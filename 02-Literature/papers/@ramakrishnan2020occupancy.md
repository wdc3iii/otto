---
type: paper
citekey: ramakrishnan2020occupancy
tags: [navigation, rl]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Ramakrishnan, Santhosh K.
- Al-Halah, Ziad
- Grauman, Kristen
year: 2020
venue: ECCV 2020
doi: 10.48550/arXiv.2008.09285
arxiv: '2008.09285'
url: https://arxiv.org/abs/2008.09285
pdf: attachments/@ramakrishnan2020occupancy.pdf
zotero: null
status: to-read
mine: false
---

# Occupancy Anticipation for Efficient Exploration and Navigation

> [!info] Santhosh K. Ramakrishnan; Ziad Al-Halah; Kristen Grauman · 2020 · ECCV 2020
> arXiv:2008.09285 (2008.09285v2, 2020-08-25) · Accepted in ECCV 2020. 19 pages, 6 figures, appendix at end

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.2 (ref `[9]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[9]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Map / geometry / potential-field anticipation as supervised learning*. **The reference for the central design choice** — mask the loss toward cells that are not currently visible.

## Your take (your words — authoritative, not ai-draft)
> **Take:** the reference for our central design choice — mask/weight the aux loss toward cells that are *not* currently visible — and evidence the unseen region is learnable at useful accuracy.

## Abstract (from arXiv)
State-of-the-art navigation methods leverage a spatial memory to generalize to new environments, but
their occupancy maps are limited to capturing the geometric structures directly observed by the
agent. We propose occupancy anticipation, where the agent uses its egocentric RGB-D observations to
infer the occupancy state beyond the visible regions. In doing so, the agent builds its spatial
awareness more rapidly, which facilitates efficient exploration and navigation in 3D environments.
By exploiting context in both the egocentric views and top-down maps our model successfully
anticipates a broader map of the environment, with performance significantly better than strong
baselines. Furthermore, when deployed for the sequential decision-making tasks of exploration and
navigation, our model outperforms state-of-the-art methods on the Gibson and Matterport3D datasets.
Our approach is the winning entry in the 2020 Habitat PointNav Challenge. Project page:
http://vision.cs.utexas.edu/projects/occupancy_anticipation/

## Concepts
- [[occupancy-anticipation]]
- [[auxiliary-task-learning]]
- [[mapless-navigation]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/2008.09285 (2008.09285v2, published 2020-08-21, updated 2020-08-25)
- DOI: https://doi.org/10.48550/arXiv.2008.09285
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.2.
