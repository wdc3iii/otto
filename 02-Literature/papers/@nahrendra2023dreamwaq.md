---
type: paper
citekey: nahrendra2023dreamwaq
tags: [locomotion, rl]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Nahrendra, I Made Aswin
- Yu, Byeongho
- Myung, Hyun
year: 2023
venue: ICRA 2023
doi: 10.48550/arXiv.2301.10602
arxiv: '2301.10602'
url: https://arxiv.org/abs/2301.10602
pdf: attachments/@nahrendra2023dreamwaq.pdf
zotero: null
status: to-read
mine: false
---

# DreamWaQ: Learning Robust Quadrupedal Locomotion With Implicit Terrain Imagination via Deep Reinforcement Learning

> [!info] I Made Aswin Nahrendra; Byeongho Yu; Hyun Myung · 2023 · ICRA 2023
> arXiv:2301.10602 (2301.10602v2, 2023-03-03) · Accepted for ICRA 2023

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.3 (ref `[14]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[14]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Legged robotics: reconstructing privileged information from a recurrent state*. Precedent for supervised heads sharing a graph with **PPO** (not BC).

## Your take (your words — authoritative, not ai-draft)
> **Take:** precedent for supervised heads sharing a graph with PPO (rather than with BC).

## Abstract (from arXiv)
Quadrupedal robots resemble the physical ability of legged animals to walk through unstructured
terrains. However, designing a controller for quadrupedal robots poses a significant challenge due
to their functional complexity and requires adaptation to various terrains. Recently, deep
reinforcement learning, inspired by how legged animals learn to walk from their experiences, has
been utilized to synthesize natural quadrupedal locomotion. However, state-of-the-art methods
strongly depend on a complex and reliable sensing framework. Furthermore, prior works that rely only
on proprioception have shown a limited demonstration for overcoming challenging terrains, especially
for a long distance. This work proposes a novel quadrupedal locomotion learning framework that
allows quadrupedal robots to walk through challenging terrains, even with limited sensing
modalities. The proposed framework was validated in real-world outdoor environments with varying
conditions within a single run for a long distance.

## Concepts
- [[auxiliary-task-learning]]
- [[state-estimation]]
- [[rl-for-legged-locomotion]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/2301.10602 (2301.10602v2, published 2023-01-25, updated 2023-03-03)
- DOI: https://doi.org/10.48550/arXiv.2301.10602
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.3.
