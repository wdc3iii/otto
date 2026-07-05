---
type: paper
citekey: molnar2023composing
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- T. G. Molnar
- A. D. Ames
year: 2023
venue: LCSS
doi: 10.1109/lcsys.2023.3339719
arxiv: 2309.06647
url: https://arxiv.org/abs/2309.06647
zotero: null
status: to-read
summary: ai-draft
pdf: attachments/@molnar2023composing.pdf
mine: false
bibkeys:
- TamasLCSS23
---

# Composing Control Barrier Functions for Complex Safety Specifications

> [!info] T. G. Molnar; A. D. Ames · 2023 · LCSS

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Encodes a Boolean composition of state constraints as a single continuously differentiable control barrier function, enabling safety-critical control under complex, compound safety specifications.

**Problem** — Real control systems must remain safe with respect to complex combinations (AND/OR) of many state constraints, but naive composition of individual CBFs yields non-smooth safe-set boundaries (min/max), which break the smoothness that CBF-QP safety filters assume.

**Method** — The authors formulate safety specifications as Boolean compositions of state constraints and give an algorithmic construction of a single smooth CBF that captures the whole specification. Non-smooth min/max operators over the constituent constraint functions are replaced by smooth over/under-approximations, yielding one continuously differentiable CBF whose zero-superlevel set encodes the composite safe set.

**Key results** — They characterize the properties of the constructed CBF and demonstrate the framework's efficacy in numerical simulations (no experimental hardware numbers in the abstract).

## Takeaways
- Turns a logical (Boolean) safety spec into a single smooth CBF, so a standard CBF-QP filter can enforce compound constraints without handling non-smoothness explicitly.
- The key trick is smooth approximation of min/max over constituent constraints; the approximation introduces conservatism, a design knob to be aware of.
- Validated in simulation only in this letter.

## Relevance to your work
For a control researcher, this is a foundational construction for enforcing several simultaneous safety constraints (e.g., joint limits, footholds, obstacle avoidance) through one smooth CBF, directly relevant to safety-filter design as in [[@cohen2025safety]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@cohen2025safety]]
- bibkeys: `TamasLCSS23`
