---
type: paper
citekey: ravi2024sam
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Ravi, Nikhila
- Gabeur, Valentin
- Hu, Yuan-Ting
- Hu, Ronghang
- Ryali, Chaitanya
- Ma, Tengyu
- Khedr, Haitham
- R\"adle, Roman
- Rolland, Chloe
- Gustafson, Laura
- others
year: 2024
venue: arXiv preprint arXiv:2408.00714
doi: null
arxiv: '2408.00714'
url: https://arxiv.org/abs/2408.00714
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@ravi2024sam.pdf
bibkeys:
- ravi2024sam
---

# Sam 2: Segment anything in images and videos

> [!info] Ravi, Nikhila; Gabeur, Valentin; Hu, Yuan-Ting; Hu, Ronghang; Ryali, Chaitanya; Ma, Tengyu · 2024 · arXiv preprint arXiv:2408.00714

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — SAM 2 is a promptable foundation model for visual segmentation that extends Segment Anything from images to video with a streaming-memory transformer.
**Problem** — Prior segmentation models (SAM) handle single images; promptable segmentation across video frames, in real time, with minimal user interaction, was unsolved.
**Method** — A simple transformer architecture augmented with streaming memory enables real-time video processing; a data engine improves model and data via user interaction, yielding the largest video segmentation dataset to date.
**Key results** — In video segmentation, better accuracy with 3x fewer interactions than prior approaches; in image segmentation, more accurate and 6x faster than the original SAM. Model, dataset, and training code released.

## Takeaways
- General-purpose promptable segmentation for images and video from a single streaming-memory transformer.
- The data-engine + interactive-annotation loop is as important as the architecture for reaching scale.
- A perception/vision tool, not a control result — relevant as an off-the-shelf module.

## Relevance to your work
A perception primitive: cited by [[@hierarchies2025motion]] presumably for segmenting terrain/obstacles or objects to feed a motion hierarchy, decoupling vision from the control stack.

## Concepts
## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `ravi2024sam`
- arXiv: https://arxiv.org/abs/2408.00714
