---
type: paper
citekey: ho2020denoising
tags: []
aliases: []
created: '2026-07-26'
modified: '2026-07-26'
authors:
- Ho, Jonathan
- Jain, Ajay
- Abbeel, Pieter
year: 2020
venue: NeurIPS
doi: 10.48550/arXiv.2006.11239
arxiv: '2006.11239'
url: https://arxiv.org/abs/2006.11239
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@ho2020denoising.pdf
---

# Denoising Diffusion Probabilistic Models

> [!info] Ho, Jonathan; Jain, Ajay; Abbeel, Pieter · 2020 · NeurIPS

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Diffusion probabilistic models — latent-variable models inspired by nonequilibrium thermodynamics — are trained on a weighted variational bound to produce high-quality image synthesis, reaching a state-of-the-art FID of 3.17 on unconditional CIFAR10.
**Problem** — Diffusion probabilistic models were a known but under-realized class of generative models; the paper targets producing high-quality samples from them and connecting them to related generative-modeling ideas.
**Method** — Train on a weighted variational bound designed from a novel connection between diffusion probabilistic models and denoising score matching with Langevin dynamics. The resulting models naturally admit a progressive lossy decompression scheme that can be interpreted as a generalization of autoregressive decoding.
**Key results** — On unconditional CIFAR10, an Inception score of 9.46 and a state-of-the-art FID of 3.17. On 256×256 LSUN, sample quality similar to ProgressiveGAN. Implementation released at https://github.com/hojonathanho/diffusion.
**Limitations** — The abstract states none; the well-known cost of iterative denoising (many sampling steps per sample) is not discussed here (inferred).

## Concepts
[[diffusion-model]]
> proposed link — concept note to be created centrally.

## Relevance to your work
This is the foundational DDPM formulation behind the diffusion policies and BeyondMimic-style ([[@liao2025beyondmimic]]) guided-diffusion skill composition now used in humanoid whole-body control — the generative engine underneath methods you'd deploy on the Unitree G1.

## Abstract (from arXiv)
We present high quality image synthesis results using diffusion probabilistic models, a class of latent variable models inspired by considerations from nonequilibrium thermodynamics. Our best results are obtained by training on a weighted variational bound designed according to a novel connection between diffusion probabilistic models and denoising score matching with Langevin dynamics, and our models naturally admit a progressive lossy decompression scheme that can be interpreted as a generalization of autoregressive decoding. On the unconditional CIFAR10 dataset, we obtain an Inception score of 9.46 and a state-of-the-art FID score of 3.17. On 256x256 LSUN, we obtain sample quality similar to ProgressiveGAN. Our implementation is available at https://github.com/hojonathanho/diffusion

## Source
- arXiv: https://arxiv.org/abs/2006.11239
- PDF: https://arxiv.org/pdf/2006.11239
- DOI: https://doi.org/10.48550/arXiv.2006.11239
