---
type: paper
citekey: kirillov2023segment
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Kirillov, Alexander
- Mintun, Eric
- Ravi, Nikhila
- Mao, Hanzi
- Rolland, Chloe
- Gustafson, Laura
- Xiao, Tete
- Whitehead, Spencer
- Berg, Alexander C.
- Lo, Wan-Yen
- Doll\'ar, Piotr
- Girshick, Ross
year: 2023
venue: arXiv:2304.02643
doi: null
arxiv: '2304.02643'
url: https://arxiv.org/abs/2304.02643
summary: ai-draft
pdf: attachments/@kirillov2023segment.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- kirillov2023segany
---

# Segment Anything

> [!info] Kirillov, Alexander; Mintun, Eric; Ravi, Nikhila; Mao, Hanzi; Rolland, Chloe; Gustafson, Laura · 2023 · arXiv:2304.02643

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A promptable foundation model for image segmentation (SAM), trained on a billion-mask dataset, that transfers zero-shot to new image distributions and segmentation tasks.
**Problem** — Segmentation models have historically been task- and dataset-specific; there was no general, promptable model that could segment "anything" and generalize zero-shot the way NLP foundation models do.
**Method** — The authors define a promptable segmentation task, build an efficient model (SAM) that accepts prompts (points, boxes, masks), and use it in a data-collection loop to bootstrap the SA-1B dataset. The model is designed so prompting enables zero-shot transfer to downstream tasks.
**Key results** — SA-1B contains over 1 billion masks on 11M licensed, privacy-respecting images. Zero-shot performance is reported as often competitive with or superior to prior fully supervised results across numerous tasks. Model and dataset released openly.

## Takeaways
- Establishes the "promptable foundation model" recipe for vision segmentation; the data engine (model-in-the-loop annotation) is as central as the architecture.
- Zero-shot generalization is the headline claim — SAM is meant as a reusable perception primitive, not an end-task model.
- Limitation: it is a 2D image-segmentation model with no notion of dynamics, geometry, or control; downstream use requires a separate pipeline.

## Relevance to your work
A locomotion/planning researcher cites SAM as an off-the-shelf perception front-end — segmenting terrain, obstacles, or footholds from camera images to feed a downstream planner such as the one in [[@csomayshanklin2025dynamically]]. It is the perception layer, not the control layer.

## Concepts


## Source
- Cited by [[@csomayshanklin2025dynamically]]
- bibkeys: `kirillov2023segany`
- arXiv: https://arxiv.org/abs/2304.02643
