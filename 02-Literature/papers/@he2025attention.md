---
type: paper
citekey: he2025attention
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- He, Junzhe
- Zhang, Chong
- Jenelten, Fabian
- Grandia, Ruben
- B\"acher, Moritz
- Hutter, Marco
year: 2025
venue: Science Robotics
doi: 10.1126/scirobotics.adv3604
arxiv: 2506.09588
url: https://arxiv.org/abs/2506.09588
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@he2025attention.pdf
bibkeys:
- he2025attention
- he_attention-based_2025
---

# Attention-based map encoding for learning generalized legged locomotion

> [!info] He, Junzhe; Zhang, Chong; Jenelten, Fabian; Grandia, Ruben; B\"acher, Moritz; Hutter, Marco · 2025 · Science Robotics
> [!info]- otto authors: [[marco-hutter]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — An attention-based encoder for local elevation maps that lets a single RL locomotion policy generalize across sparse-foothold and diverse terrains without hand-crafted terrain features.
**Problem** — Dynamic legged locomotion needs precise foothold planning when footholds are sparse, robustness to uncertainty/disturbance, and generalization across terrains; conventional fixed map encodings (e.g. CNN over heightmaps) struggle to capture the task-relevant terrain structure across all of these at once.
**Method** — The controller is trained by reinforcement learning with an attention mechanism that encodes the surrounding terrain map, letting the policy attend to the salient terrain regions (e.g. viable footholds) rather than compressing the whole map uniformly.
**Key results** — Demonstrates generalized locomotion controllers across challenging and diverse terrain (published in Science Robotics, 2025); see paper for hardware and benchmark details.

## Takeaways
- Attention over the heightmap is the key inductive bias: it selects relevant terrain structure, improving foothold precision and cross-terrain generalization vs. dense CNN encodings.
- A single learned policy replaces terrain-specific tuning — the generalization claim, not raw agility, is the contribution.
- From the Hutter group (ANYmal lineage); complements DTC-style approaches by pushing map perception into the learned policy rather than an external planner.

## Relevance to your work
A state-of-the-art example of terrain-aware RL locomotion where perception (map encoding) is baked into the policy — a natural point of comparison for reference-guided or hierarchical schemes like [[@dai2025walk]] that keep planning and learning more separated.

## Concepts


## Source
- Cited by [[@dai2025walk]], [[@terrain2026consistent]]
- bibkeys: `he2025attention`, `he_attention-based_2025`
