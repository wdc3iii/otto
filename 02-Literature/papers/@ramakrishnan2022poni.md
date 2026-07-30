---
type: paper
citekey: ramakrishnan2022poni
tags: [navigation, planning]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Ramakrishnan, Santhosh Kumar
- Chaplot, Devendra Singh
- Al-Halah, Ziad
- Malik, Jitendra
- Grauman, Kristen
year: 2022
venue: CVPR 2022
doi: 10.48550/arXiv.2201.10029
arxiv: '2201.10029'
url: https://arxiv.org/abs/2201.10029
pdf: attachments/@ramakrishnan2022poni.pdf
zotero: null
status: to-read
mine: false
---

# PONI: Potential Functions for ObjectGoal Navigation with Interaction-free Learning

> [!info] Santhosh Kumar Ramakrishnan; Devendra Singh Chaplot; Ziad Al-Halah; Jitendra Malik; Kristen Grauman · 2022 · CVPR 2022
> arXiv:2201.10029 (2201.10029v2, 2022-06-17) · 8 pages + supplementary. Accepted in CVPR 2022

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.2 (ref `[10]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[10]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Map / geometry / potential-field anticipation as supervised learning*. Closest precedent for treating a **geodesic/wavefront field** as a supervised target.

## Your take (your words — authoritative, not ai-draft)
> **Take:** the closest published precedent for treating "the wavefront field" as a supervised prediction target, and evidence that the supervised version is learnable given a decent map.

## Abstract (from arXiv)
State-of-the-art approaches to ObjectGoal navigation rely on reinforcement learning and typically
require significant computational resources and time for learning. We propose Potential functions
for ObjectGoal Navigation with Interaction-free learning (PONI), a modular approach that
disentangles the skills of `where to look?' for an object and `how to navigate to (x, y)?'. Our key
insight is that `where to look?' can be treated purely as a perception problem, and learned without
environment interactions. To address this, we propose a network that predicts two complementary
potential functions conditioned on a semantic map and uses them to decide where to look for an
unseen object. We train the potential function network using supervised learning on a passive
dataset of top-down semantic maps, and integrate it into a modular framework to perform ObjectGoal
navigation. Experiments on Gibson and Matterport3D demonstrate that our method achieves the
state-of-the-art for ObjectGoal navigation while incurring up to 1,600x less computational cost for
training. Code and pre-trained models are available: https://vision.cs.utexas.edu/projects/poni/

## Concepts
- [[occupancy-anticipation]]
- [[mapless-navigation]]
- [[path-conditioned-rl]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/2201.10029 (2201.10029v2, published 2022-01-25, updated 2022-06-17)
- DOI: https://doi.org/10.48550/arXiv.2201.10029
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.2.
