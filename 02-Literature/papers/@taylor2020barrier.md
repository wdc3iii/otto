---
type: paper
citekey: taylor2020barrier
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Taylor, Andrew J
- Singletary, Andrew
- Yue, Yisong
- Ames, Aaron D
year: 2020
venue: IEEE Control Systems Letters
doi: 10.1109/LCSYS.2020.3009082
arxiv: 2003.08028
url: https://arxiv.org/abs/2003.08028
summary: ai-draft
pdf: attachments/@taylor2020barrier.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- taylor2020control
---

# A control barrier perspective on episodic learning via projection-to-state safety

> [!info] Taylor, Andrew J; Singletary, Andrew; Yue, Yisong; Ames, Aaron D · 2020 · IEEE Control Systems Letters

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Introduces Projection-to-State Safety (PSSf), an ISS-style notion that quantifies how model uncertainty in a CBF's derivative degrades safety, and shows episodic learning can shrink that uncertainty with provable safety improvement.

**Problem** — CBFs guarantee safety only under an accurate model; model error in the CBF time derivative erodes the guarantee, and there was no principled way to quantify how much learning could restore it.

**Method** — The paper defines PSSf, characterizing safety degradation in terms of a projected disturbance (analogous to input-to-state stability for safety), then couples it with an episodic learning scheme that reduces the derivative-model uncertainty. This yields explicit translations from learning-error bounds to bounds on safety degradation.

**Key results** — Demonstrates that a practical episodic learning approach reduces uncertainty and tightens safety guarantees, validated in simulation and on hardware.

## Takeaways
- PSSf gives a quantitative bridge: bounded learning error ⇒ bounded safety violation, making "learn the model, keep the CBF" rigorous.
- The projected-disturbance framing mirrors ISS, so familiar robustness tools transfer to safety analysis.

## Relevance to your work
Directly relevant to learning-augmented safety-critical control: it formalizes how much a learned residual can be trusted inside a CBF, central to the learning-plus-guarantees theme in [[@compton2025learning]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025learning]]
- bibkeys: `taylor2020control`
