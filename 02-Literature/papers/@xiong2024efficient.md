---
type: paper
citekey: xiong2024efficient
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Xiong, Yunyang
- Zhou, Chong
- Xiang, Xiaoyu
- Wu, Lemeng
- Zhu, Chenchen
- Liu, Zechun
- Suri, Saksham
- Varadarajan, Balakrishnan
- Akula, Ramya
- Iandola, Forrest
- Krishnamoorthi, Raghuraman
- Soran, Bilge
year: 2024
venue: preprint arXiv:2411.18933
doi: null
arxiv: '2411.18933'
url: https://arxiv.org/abs/2411.18933
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@xiong2024efficient.pdf
bibkeys:
- xiong2024efficienttam
---

# Efficient Track Anything

> [!info] Xiong, Yunyang; Zhou, Chong; Xiang, Xiaoyu; Wu, Lemeng; Zhu, Chenchen; Liu, Zechun · 2024 · preprint arXiv:2411.18933

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — EfficientTAM delivers Segment Anything Model 2 (SAM 2)-level video object segmentation and tracking at roughly half the compute and parameters, cheap enough to run on a phone.
**Problem** — SAM 2 is a powerful "track/segment anything" model for video, but its size and inference cost limit real-time and on-device (mobile/edge) deployment.
**Method** — Revisit plain (non-hierarchical) Vision Transformers as the image encoder and introduce an efficient memory module to cut the cost of the memory/attention over past frames. Models are trained on the SA-1B and SA-V datasets for image and video segmentation.
**Key results** — Reports ~2x speedup on an A100 and ~2.4x parameter reduction versus SAM 2 for video segmentation (and ~20x on both axes versus the original SAM for image tasks), while running at ~10 FPS for video object segmentation on an iPhone 15 Pro Max.

## Takeaways
- Plain ViT encoders plus a lightweight memory module recover most of SAM 2's quality at a fraction of the cost — the efficiency comes from architecture, not distillation tricks.
- On-device (~10 FPS mobile) promptable video segmentation becomes feasible, relevant for real-time robot perception.
- A perception/vision contribution, not a control or dynamics result — cited for its tracking capability, not its methods.

## Relevance to your work
An efficient, real-time promptable video segmentation/tracking model of the kind a navigation-autonomy stack would use for object tracking in its perception layer, as in [[@hierarchies2025motion]].

## Concepts


## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `xiong2024efficienttam`
- arXiv: https://arxiv.org/abs/2411.18933
