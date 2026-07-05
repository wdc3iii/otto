---
type: paper
citekey: samuel1959some
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- A. L. Samuel
year: 1959
venue: IBM Journal of Research and Development
doi: 10.1147/rd.33.0210
arxiv: null
url: https://doi.org/10.1147/rd.33.0210
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- Samuel59
---

# Some Studies in Machine Learning Using the Game of Checkers

> [!info] A. L. Samuel · 1959 · IBM Journal of Research and Development

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A seminal demonstration that a computer can *learn* to play checkers better than its programmer, using two machine-learning procedures given only the rules, a "sense of direction," and a redundant, incomplete list of candidate features with unknown weights.
**Problem** — Could a machine improve its own performance through experience rather than being explicitly programmed with a fixed strategy?
**Method** — Two learning procedures were investigated on the game of checkers, tuning the signs and relative weights of a set of board-evaluation parameters through self-play/experience so the program discovers which features matter.
**Key results** — The program learned to play a stronger game than its author in a remarkably short time (roughly 8–10 hours of machine play); the authors argue the principles generalize far beyond checkers.

## Takeaways
- One of the founding works of machine learning and of what became reinforcement learning / self-play value-function tuning.
- Core idea — learn evaluation-function weights from experience rather than hand-specifying strategy — prefigures modern value-based RL.
- Historically important as an existence proof that learning can exceed the designer's own skill.

## Relevance to your work
A canonical origin point for the learning-from-experience paradigm underpinning modern RL-based control; cited by [[@compton2024constructive]] to situate its learning-based approach within the lineage of machine learning.

## Concepts


## Source
- Cited by [[@compton2024constructive]]
- bibkeys: `Samuel59`
