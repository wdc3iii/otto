---
type: concept
tags: [rl, to-revisit]
aliases: [sim-to-real, sim2real, zero-shot transfer]
created: 2026-07-06
modified: 2026-07-06
---

# Sim-to-real transfer

> [!note] Stub — minimal seed, expand when revisited.

## Definition
Training a policy (or model) entirely in simulation and deploying it on hardware, ideally **zero-shot** — no real-world fine-tuning. Bridged by domain randomization, privileged-to-onboard distillation, realistic sensor/actuator models, and reward/observation design that avoids exploiting sim-only cues.

## Why it matters
Sim gives billions of cheap transitions; the whole bet of RL-for-robots rides on the transfer holding. The gap shows up as behaviors that were free in sim (perfect state, no latency, idealized contacts) failing on hardware — motivating privileged critics, observation histories, and randomization.

## Grounding
- [[@wang2026guide]] — zero-shot deployment of an end-to-end nav policy (in-lab mazes + outdoor grass/vegetation), privileged sim state used only to *supervise* an auxiliary predictor at train time.
- [[@yang2025spatially]] — depth encoder pretrained as a VAE on large-scale synthetic depth (TartanAir) *for* sim-to-real robustness (latent distribution covers real data). · [[@lee2024learning]] · [[@hoeller2021learning]] · [[@roth2025learned]] · [[@zhang2026focusnav]] — sim-trained legged nav deployed on hardware.

- Locomotion side (same bet, via domain randomization): [[massively-parallel-simulation]] powers [[@compton2025dynamic|DTMPC]], [[@compton2025learning|predictive CBFs]], [[@dai2025walk|PLANC]], and [[@terrain2026consistent]] — all sim-trained and transferred by domain randomization.

## See also
- [[rl-for-legged-locomotion]] · [[massively-parallel-simulation]] · [[mapless-navigation]] · [[recurrent-navigation-policy]]
