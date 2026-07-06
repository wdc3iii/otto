---
type: paper
citekey: singletary2021comparative
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Singletary, Andrew
- Klingebiel, Karl
- Bourne, Joseph
- Browning, Andrew
- Tokumaru, Phil
- Ames, Aaron
year: 2021
venue: 2021 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)
doi: 10.1109/IROS51168.2021.9636670
arxiv: 2010.09819
url: https://arxiv.org/abs/2010.09819
summary: ai-draft
pdf: attachments/@singletary2021comparative.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- singletary2021comparative
---

# Comparative analysis of control barrier functions and artificial potential fields for obstacle avoidance

> [!info] Singletary, Andrew; Klingebiel, Karl; Bourne, Joseph; Browning, Andrew; Tokumaru, Phil; Ames, Aaron · 2021 · 2021 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Artificial potential fields (APFs) are shown to be a special case of control barrier functions (CBFs), so CBFs strictly generalize the classic obstacle-avoidance workhorse.

**Problem** — APFs have been the standard for real-time collision avoidance for ~40 years (model-independent, cheap, easy), while CBFs are a newer tool giving formal safety guarantees as a filter on a nominal controller. Their precise relationship was unclear.

**Method** — The paper draws a formal comparison between the two frameworks, proving that any APF induces a corresponding CBF while the converse does not hold, and analyzes the practical differences in obstacle avoidance for mobile robots and manipulators.

**Key results** — Establishes APFs as a strict special case of CBFs, clarifying when the added expressiveness and guarantees of CBFs are worth the extra machinery over a potential-field controller.

## Takeaways
- APF ⊂ CBF: potential fields are recoverable as one CBF construction, but CBFs admit safety certificates APFs cannot express.
- Frames the choice between the two as a spectrum rather than competing methods — useful when justifying a CBF-based safety layer.

## Relevance to your work
Grounds why a learning-based locomotion/navigation safety filter reaches for CBFs over classic potential fields; directly relevant to safety-filtered control as in [[@compton2025learning]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025learning]]
- bibkeys: `singletary2021comparative`
