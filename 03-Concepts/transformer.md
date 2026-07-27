---
type: concept
tags: [foundation-model, to-revisit]
aliases: [Transformer, self-attention, attention mechanism]
created: 2026-07-26
modified: 2026-07-26
---

# Transformer

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
The attention-based sequence architecture introduced in [[@vaswani2017attention]] that replaces recurrence and convolution with **(self-)attention**: every token attends to every other token, giving an O(1) path length between any two positions and enabling fully parallel training over sequences.

## Intuition / why it matters
Transformers scale predictably with data and compute, which is why they became the substrate for LLMs and vision-language models — and, through those, for robot policies. RT-1/RT-2 tokenize observations (and actions) and run a transformer, inheriting the web-scale pretraining of the underlying VLM. The relevance to my work is at the **semantic / high-level** layer, not the kHz control loop.

## Grounding
- Origin: [[@vaswani2017attention]] — attention-only encoder-decoder; SOTA machine translation.
- Robot policies built on it: [[@brohan2022rt1]] (Robotics Transformer), [[@brohan2023rt2]] (VLA).
- Navigation transformers already in otto: [[@shah2023vint|ViNT]] · [[@sridhar2024nomad|NoMaD]] (ViNT backbone + a [[diffusion-policy]] head).

## Related
- [[foundation-model]] · [[vision-language-action]]

## Open questions
- Attention is quadratic in sequence length — a poor fit for high-rate control loops. Is a transformer the right backbone for locomotion, or only for the planning/semantic layer above a fast low-level controller?
