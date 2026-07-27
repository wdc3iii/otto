---
type: concept
tags: [method, to-revisit]
aliases: [Vision-Language-Action model, VLA, robot foundation model]
created: 2026-07-26
modified: 2026-07-26
---

# Vision-Language-Action model

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
A robot policy built by **fine-tuning an internet-pretrained vision-language model to output actions**, so that web-scale semantic knowledge (objects, instructions, affordances) transfers into control ([[@brohan2023rt2]], [[@kim2024openvla]]). Observations and actions are tokenized and produced by the same [[transformer]] backbone.

## Intuition / why it matters
VLAs are the **semantic / task layer** — generalization to novel objects and language instructions — that would sit *above* a low-level locomotion + control stack like mine on the Unitree G1. The literature is overwhelmingly **manipulation**; the humanoid-locomotion analogue is largely open.

## Grounding
- [[@brohan2022rt1]] (RT-1) → [[@brohan2023rt2]] (RT-2, web knowledge → action).
- Data/scale: [[@oneill2024open]] (Open X-Embodiment / RT-X, cross-embodiment).
- Open + efficient: [[@kim2024openvla]] (OpenVLA, 7B). Flow-based: [[@black2024pi0]] (π0).

## Related
- [[foundation-model]] · [[transformer]]

## Open questions
- **Control-rate mismatch**: VLAs run at ~Hz; locomotion runs at ~kHz. What is the right interface between a VLA task layer and a fast low-level controller?
- What is the locomotion/whole-body analogue of a manipulation VLA?
