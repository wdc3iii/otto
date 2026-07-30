---
type: concept
tags: [rl, to-revisit]
aliases: [sim-to-real, sim2real, zero-shot transfer]
created: 2026-07-06
modified: 2026-07-29
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

- [[@xie2026grail]] — egocentric RGB policies trained on *only* synthetically generated data (visual domain randomization + camera alignment), deployed on a Unitree G1: 84% pick-up, 90% stair-climbing. Tethered 10 Hz inference, not onboard.
- [[@araujo2025retargeting]] — a warning about attributing transfer failures to the sim2real gap: with reward tuning suppressed, much of the robustness loss traces to **artifacts in the retargeted reference data** (ground penetration, self-intersection, velocity spikes), not to sim fidelity. Evaluated 4096× with domain randomization + MuJoCo sim2sim.
- [[@luo2025sonic]] — 123 real motion sequences: 99.2% success (vs. 100% sim), MPJPE-L 25.7 mm (vs. 22.3 mm), **fully onboard** on a Jetson Orin at 50 Hz. Useful decomposition of *where* the gap lives: upper body 22.2 vs. 21.8 mm, but **feet 53.7 vs. 29.0 mm** — precise foot placement under real contact dynamics is the residual.

- Locomotion side (same bet, via domain randomization): [[massively-parallel-simulation]] powers [[@compton2025dynamic|DTMPC]], [[@compton2025learning|predictive CBFs]], [[@dai2025walk|PLANC]], and [[@terrain2026consistent]] — all sim-trained and transferred by domain randomization.

## See also
- [[rl-for-legged-locomotion]] · [[massively-parallel-simulation]] · [[mapless-navigation]] · [[recurrent-navigation-policy]]
