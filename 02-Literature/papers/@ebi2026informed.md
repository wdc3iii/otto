---
type: paper
citekey: ebi2026informed
tags: [rl, method]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Ebi, Daniel
- Ernst, Damien
- Böhm, Klemens
- Lambrechts, Gaspard
year: 2025
venue: ICML 2026
doi: 10.48550/arXiv.2509.26000
arxiv: '2509.26000'
url: https://arxiv.org/abs/2509.26000
pdf: attachments/@ebi2026informed.pdf
zotero: null
status: to-read
mine: false
---

# Informed Asymmetric Actor-Critic: Leveraging Privileged Signals Beyond Full-State Access

> [!info] Daniel Ebi; Damien Ernst; Klemens Böhm; Gaspard Lambrechts · 2025 · ICML 2026
> arXiv:2509.26000 (2509.26000v3, 2026-06-09) · Accepted at ICML 2026

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.4 (ref `[24]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[24]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Memory, POMDPs, privileged information, and cautions*. **Keeps the bookkeeping honest**: privileged critic = unbiased asymmetry; an actor-side aux head is a different lever.

## Your take (your words — authoritative, not ai-draft)
> **Take:** keeps the bookkeeping honest — our privileged critic map is *unbiased* asymmetry, whereas an actor-side aux head deliberately biases the actor's representation. Different levers; do not conflate them when reporting.

## Abstract (from arXiv)
Asymmetric reinforcement learning leverages privileged information available during training to
improve learning under partial observability. Existing asymmetric actor-critic methods typically
assume access to the full environment state to condition the critic during training, which is often
unrealistic in practice. We introduce the informed asymmetric actor-critic framework that allows the
critic to be conditioned on arbitrary state-dependent privileged signals, and show that any such
signal yields unbiased policy gradient estimates. This substantially expands the set of admissible
privileged information and raises the problem of selecting the most informative signals for
learning. To this end, we propose two novel informativeness criteria: a dependence-based test that
can be applied prior to training, and a test based on improvements in value prediction that can be
applied post hoc. Experiments on partially observable benchmarks and synthetic environments
demonstrate that carefully selected privileged signals can match or outperform full-state asymmetric
baselines while relying on strictly less state information.

## Concepts
- [[privileged-information]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/2509.26000 (2509.26000v3, published 2025-09-30, updated 2026-06-09)
- DOI: https://doi.org/10.48550/arXiv.2509.26000
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.4.
