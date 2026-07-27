---
type: concept
tags: [generative, imitation, to-revisit]
aliases: [Diffusion policy, action diffusion]
created: 2026-07-26
modified: 2026-07-26
---

# Diffusion policy

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
A visuomotor imitation-learning approach where the policy is a **conditional [[diffusion-model]] over action sequences**: instead of regressing a single action, it denoises a chunk of future actions conditioned on observations ([[@chi2023diffusion]]).

## Intuition / why it matters
Representing actions as a diffusion process handles **multimodal demonstrations** gracefully and trains stably, which is why it became a strong from-scratch baseline for manipulation — VLAs like [[@kim2024openvla|OpenVLA]] explicitly benchmark against it. Most demonstrations to date are quasi-static manipulation; the open question is dynamic, underactuated locomotion.

## Grounding
- [[@chi2023diffusion]] — Diffusion Policy: visuomotor policy learning via action diffusion.
- Builds on [[diffusion-model]] ([[@ho2020denoising]]).
- **In navigation (already in otto):** [[@sridhar2024nomad|NoMaD]] attaches a diffusion action head to the ViNT [[transformer]] — a diffusion policy sitting in this vault's nav cluster.
- **Beyond quasi-static manipulation:** [[@liao2025beyondmimic|BeyondMimic]] uses *guided* diffusion for dynamic humanoid whole-body skills on hardware — the counterexample to the manipulation-only caveat below.

## Related
- [[diffusion-model]] · [[motion-imitation]]

## Open questions
- Receding-horizon action-chunk execution and latency under real-time control.
- Does the paradigm transfer from quasi-static manipulation to contact-rich dynamic locomotion, where my [[control-lyapunov-function|CLF]]/[[control-barrier-function|CBF]]-based guarantees live?
