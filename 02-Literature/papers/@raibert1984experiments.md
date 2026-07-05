---
type: paper
citekey: raibert1984experiments
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Raibert, Marc H
- Brown Jr, H Benjamin
- Chepponis, Michael
year: 1984
venue: The International Journal of Robotics Research
doi: 10.1177/027836498400300207
arxiv: null
url: https://doi.org/10.1177/027836498400300207
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- raibert1984experiments
- raibert_experiments_1984
---

# Experiments in balance with a 3D one-legged hopping machine

> [!info] Raibert, Marc H; Brown Jr, H Benjamin; Chepponis, Michael · 1984 · The International Journal of Robotics Research

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Seminal demonstration that a physical 3D one-legged hopping machine can balance and run on an open floor using three simple decoupled control laws.
**Problem** — Balance in legged locomotion was understood only for planar, mechanically constrained hoppers; it was unclear whether the same simple principles extend to unconstrained 3D running.
**Method** — Control of the machine is decomposed into three separate parts: one regulating forward running velocity, one regulating body attitude, and one regulating hopping height. Each is a relatively simple algorithm acting on a springy telescoping leg.
**Key results** — The physical 3D hopper hopped in place, ran at a desired rate, and traveled along a simple path — establishing that decoupled, low-complexity control suffices for dynamic 3D balance.

## Takeaways
- The foundational "template" of dynamic legged locomotion: a spring-loaded hopping leg with velocity/attitude/height decoupled into three simple loops.
- Balance emerges from dynamics + minimal feedback, not from full-model inversion — the intellectual root of reduced-order / hopping-template control.
- Simplicity is the point: the same three-part decomposition later generalized to quadrupeds and bipeds.

## Relevance to your work
The origin of reduced-order, template-based legged control that later work formalizes; cited by [[@compton2025dynamic]] and related locomotion papers as the historical anchor for simple-model gait generation.

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@compton2025dynamic]], [[@compton2025learning]], [[@csomayshanklin2024robust]], [[@hierarchies2025motion]]
- bibkeys: `raibert1984experiments`, `raibert_experiments_1984`
