---
type: paper
citekey: mitchell1980need
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- T. M. Mitchell
year: 1980
venue: null
doi: null
arxiv: null
url: https://www.cs.cmu.edu/~tom/pubs/NeedForBias_1980.pdf
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@mitchell1980need.pdf
bibkeys:
- mitchell80
---

# The Need for Biases in Learning Generalizations

> [!info] T. M. Mitchell · 1980 · —

## Summary
> [!note] AI-drafted from the source (Rutgers CBM-TR-117; the report has no formal abstract) — a base to refine.
**TL;DR** — Generalization from examples is impossible without bias: a learner's ability to classify unseen instances depends entirely on the assumptions (biases) it brings to the data.
**Problem** — Formalizes why inductive learning cannot work from data alone — what does it take for a system to generalize beyond the examples it has seen?
**Method** — Frames generalization in terms of the version space of hypotheses consistent with the training data. A "bias" is defined as any basis for preferring one consistent generalization over another (e.g., restricting the hypothesis language or ranking hypotheses). Analyzes what a purely unbiased learner could and could not do.
**Key results** — A completely unbiased learner can only reproduce labels it has already seen and is "nearly useless" for prediction; therefore bias is not a defect but a prerequisite for generalization, and the central design question becomes which biases to adopt and how to justify them.

## Takeaways
- Foundational statement of inductive bias: no generalization without assumptions — later crystallized as the "no free lunch" intuition.
- Recasts learner design as the deliberate choice and justification of biases (hypothesis-space restriction, preference orderings) rather than bias elimination.
- Conceptual/theoretical position paper, not an empirical result.

## Relevance to your work
Classic ML foundation cited to justify structural/inductive assumptions (e.g., reduced-order or model-based priors) in learning-based controllers — a policy-learning method's guarantees and sample efficiency come from the biases it builds in, as in the structured designs of [[@compton2024constructive]].

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@compton2024constructive]]
- bibkeys: `mitchell80`
