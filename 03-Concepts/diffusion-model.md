---
type: concept
tags: [generative, to-revisit]
aliases: [Diffusion model, DDPM, denoising diffusion, score-based generative model]
created: 2026-07-26
modified: 2026-07-29
---

# Diffusion model

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
A generative model that learns to **reverse a gradual noising (diffusion) process**: training corrupts data toward Gaussian noise, and the model learns to denoise; sampling runs the reverse chain from noise back to a data sample ([[@ho2020denoising]]).

## Intuition / why it matters
Diffusion captures **expressive, multimodal distributions** with stable training (unlike GANs). In robotics this is used to model *action* distributions ([[@chi2023diffusion|diffusion policy]]) and *motion skills* ([[@liao2025beyondmimic|BeyondMimic]] uses guided latent diffusion to compose humanoid skills). Flow-matching models like [[@black2024pi0|π0]] are a close, faster cousin.

## Grounding
- Foundational: [[@ho2020denoising]] (DDPM).
- Applied to control/motion: [[@chi2023diffusion]] · [[@liao2025beyondmimic]] · [[@black2024pi0]].
- As a VLA **action head**: [[@bjorck2025gr00t]] (GR00T N1 — a diffusion transformer is "System 1," generating motor actions in real time under a vision-language module).
- Estimation *as* constrained generation: [[@li2025genmo]] (GENMO — regression + diffusion in one model; motion estimation reformulated as generation whose output must satisfy the observation).

## Related
- [[diffusion-policy]] · [[motion-imitation]]

## Open questions
- Iterative denoising is **slow** — a real problem for real-time control. Distillation / consistency models / flow matching are the responses; do they hold up for dynamic legged control?
