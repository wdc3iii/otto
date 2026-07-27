---
type: paper
citekey: chi2023diffusion
tags: []
aliases: []
created: '2026-07-26'
modified: '2026-07-26'
authors:
- Chi, Cheng
- Xu, Zhenjia
- Feng, Siyuan
- Cousineau, Eric
- Du, Yilun
- Burchfiel, Benjamin
- Tedrake, Russ
- Song, Shuran
year: 2023
venue: RSS
doi: 10.48550/arXiv.2303.04137
arxiv: '2303.04137'
url: https://arxiv.org/abs/2303.04137
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@chi2023diffusion.pdf
---

# Diffusion Policy: Visuomotor Policy Learning via Action Diffusion

> [!info] Chi, Cheng; Xu, Zhenjia; Feng, Siyuan; Cousineau, Eric; Du, Yilun; Burchfiel, Benjamin; Tedrake, Russ; Song, Shuran · 2023 · RSS

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — Represents a robot's visuomotor policy as a *conditional denoising diffusion process* over action sequences. Benchmarked across 12 tasks from 4 manipulation benchmarks, it consistently beats prior state-of-the-art robot learning methods by an average of 46.9%.

**Problem** — Common visuomotor policy representations struggle with multimodal action distributions, high-dimensional action spaces, and unstable training. The paper asks how to learn robust visuomotor manipulation policies that handle all three.

**Method** — Model the policy as a conditional denoising diffusion process: instead of regressing an action directly, learn the gradient of the action-distribution score function and iteratively refine an action sample at inference via a series of stochastic Langevin dynamics steps, conditioned on observations. Three key technical contributions make diffusion practical for physical-robot visuomotor control: receding-horizon control (predict an action sequence, execute part of it, re-plan (inferred)), visual conditioning (condition the denoising on visual observations), and a time-series diffusion transformer architecture.

**Key results** — Consistently outperforms existing state-of-the-art robot learning methods across 12 tasks / 4 benchmarks, with an average improvement of 46.9%. The diffusion formulation gracefully handles multimodal action distributions, scales to high-dimensional action spaces, and exhibits stable training. Code, data, and training details are released publicly.

**Limitations** — The abstract does not enumerate limitations (inferred). Iterative denoising at inference adds compute/latency relative to single-shot regression policies (inferred), and evaluation targets tabletop manipulation benchmarks rather than legged or whole-body locomotion (inferred).

## Concepts

[[diffusion-model]], [[diffusion-policy]]

> proposed links — concept notes to be created centrally.

## Relevance to your work
Diffusion policies are now a leading paradigm for learned visuomotor control, so this is the canonical reference for the approach. In contrast to your CLF/CBF-based control on the Unitree G1, it offers no stability or safety certificates but excels at representing multimodal, high-DoF action distributions from demonstrations.

## Abstract (from arXiv)
This paper introduces Diffusion Policy, a new way of generating robot behavior by representing a robot's visuomotor policy as a conditional denoising diffusion process. We benchmark Diffusion Policy across 12 different tasks from 4 different robot manipulation benchmarks and find that it consistently outperforms existing state-of-the-art robot learning methods with an average improvement of 46.9%. Diffusion Policy learns the gradient of the action-distribution score function and iteratively optimizes with respect to this gradient field during inference via a series of stochastic Langevin dynamics steps. We find that the diffusion formulation yields powerful advantages when used for robot policies, including gracefully handling multimodal action distributions, being suitable for high-dimensional action spaces, and exhibiting impressive training stability. To fully unlock the potential of diffusion models for visuomotor policy learning on physical robots, this paper presents a set of key technical contributions including the incorporation of receding horizon control, visual conditioning, and the time-series diffusion transformer. We hope this work will help motivate a new generation of policy learning techniques that are able to leverage the powerful generative modeling capabilities of diffusion models. Code, data, and training details are publicly available.

## Source
- arXiv (abs): https://arxiv.org/abs/2303.04137
- arXiv (pdf): https://arxiv.org/pdf/2303.04137
- DOI: https://doi.org/10.48550/arXiv.2303.04137
