---
type: paper
citekey: vaswani2017attention
tags: [foundation-model]
aliases: []
created: '2026-07-26'
modified: '2026-07-26'
authors:
- Vaswani, Ashish
- Shazeer, Noam
- Parmar, Niki
- Uszkoreit, Jakob
- Jones, Llion
- Gomez, Aidan N.
- Kaiser, Lukasz
- Polosukhin, Illia
year: 2017
venue: NeurIPS
doi: 10.48550/arXiv.1706.03762
arxiv: '1706.03762'
url: https://arxiv.org/abs/1706.03762
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@vaswani2017attention.pdf
---

# Attention Is All You Need

> [!info] Vaswani, Ashish; Shazeer, Noam; Parmar, Niki; Uszkoreit, Jakob; Jones, Llion; Gomez, Aidan N.; Kaiser, Lukasz; Polosukhin, Illia · 2017 · NeurIPS

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Introduces the Transformer, a sequence-transduction architecture built entirely on attention mechanisms, dispensing with recurrence and convolutions; it is more parallelizable, trains faster, and sets new state-of-the-art translation quality.
**Problem** — Dominant sequence-transduction models rely on complex recurrent or convolutional encoder-decoder networks (the best also coupling them via attention); their sequential nature limits parallelization and inflates training time.
**Method** — A "simple" encoder-decoder architecture based solely on attention, with no recurrence or convolution. (inferred) The core mechanism is multi-head self-attention plus position-wise feed-forward layers, with positional encodings to inject sequence order — the abstract itself only states the model is attention-only and encoder-decoder.
**Key results** — Achieves 28.4 BLEU on WMT 2014 English-to-German, improving over prior best results (including ensembles) by over 2 BLEU; establishes a new single-model state-of-the-art of 41.8 BLEU on WMT 2014 English-to-French after 3.5 days of training on eight GPUs, at a small fraction of the best models' training cost. Generalizes to English constituency parsing under both large and limited training data.
**Limitations** — Not discussed in the abstract; evaluation is limited to machine translation and constituency parsing. (inferred) The canonical known caveat is that self-attention cost is quadratic in sequence length.

## Concepts
[[transformer]]
> proposed link — concept note to be created centrally.

## Relevance to your work
The Transformer is the backbone of the VLA / sequence-model era of robot policies, so it grounds the architecture underlying modern learned controllers relevant to humanoid locomotion & navigation autonomy on the Unitree G1. Understanding attention here is prerequisite to reasoning about how such policies fuse perception and action versus classical planning/control.

## Abstract (from arXiv)
The dominant sequence transduction models are based on complex recurrent or convolutional neural networks in an encoder-decoder configuration. The best performing models also connect the encoder and decoder through an attention mechanism. We propose a new simple network architecture, the Transformer, based solely on attention mechanisms, dispensing with recurrence and convolutions entirely. Experiments on two machine translation tasks show these models to be superior in quality while being more parallelizable and requiring significantly less time to train. Our model achieves 28.4 BLEU on the WMT 2014 English-to-German translation task, improving over the existing best results, including ensembles by over 2 BLEU. On the WMT 2014 English-to-French translation task, our model establishes a new single-model state-of-the-art BLEU score of 41.8 after training for 3.5 days on eight GPUs, a small fraction of the training costs of the best models from the literature. We show that the Transformer generalizes well to other tasks by applying it successfully to English constituency parsing both with large and limited training data.

## Source
- arXiv: https://arxiv.org/abs/1706.03762
- PDF: https://arxiv.org/pdf/1706.03762
- DOI: https://doi.org/10.48550/arXiv.1706.03762
