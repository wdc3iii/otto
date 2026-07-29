---
type: concept
tags: [locomotion, to-revisit]
aliases: [Loco-manipulation, whole-body loco-manipulation, mobile manipulation]
created: 2026-07-29
modified: 2026-07-29
---

# Loco-manipulation

> [!note] AI-drafted stub, created 2026-07-29 alongside [[@xie2026grail]] — the vault referenced
> loco-manipulation from two paper notes but had no concept note for it. Refine or reject; if you'd
> rather this live as a section inside an existing note, say so and I'll fold it back.

## Definition
Tasks where **locomotion and manipulation cannot be decoupled** — the robot must coordinate whole-body
balance, external contact with objects, and scene-aware stepping *simultaneously*. Distinct from mobile
manipulation on a stable wheeled base: for a humanoid, reaching, carrying, or pushing changes the momentum
and support constraints that keep it upright, so the manipulation objective and the balance objective share
the same actuators and the same contact budget.

## Intuition / why it matters
This is the axis along which "humanoid" stops being a locomotion problem. Two consequences worth holding onto:
- **Contact is the coupling.** Hands become load-bearing or force-applying contacts, which perturbs the
  support polygon and centroidal dynamics that locomotion controllers assume. [[@lin2021long]] makes the
  related point from the navigation side — treating hands as first-class contacts for balance, not only feet.
- **Data, not architecture, is the current bottleneck.** Whole-body references that are *both* physically
  feasible *and* executable on the target robot are expensive: teleoperation and mocap don't scale, and video
  reconstruction is underconstrained. [[@xie2026grail]] is an attempt to generate that data entirely in
  simulation.

## Grounding
- **Model-based references + RL tracking:** [[@liu2025opt2skill]] (Opt2Skill — trajectory optimization supplies
  dynamically feasible, contact-consistent whole-body references; RL tracks them on Digit).
- **Generated data + tracking on a pretrained controller:** [[@xie2026grail]] (GRAIL — 4D human–object
  interaction reconstructed from VFM-generated video, retargeted to a Unitree G1; object-aware latent adaptor
  for manipulation, height-map-conditioned tracker for terrain).
- **Hands as contacts for navigation over rubble:** [[@lin2021long]].

## Related
- [[motion-imitation]] — the dominant route to loco-manipulation policies is tracking whole-body references,
  so the imitation lineage and its open questions carry over directly.
- [[rl-for-legged-locomotion]] · [[sim-to-real-transfer]]

## Open questions
- Where do the reference motions come from, and does the answer change the guarantees? [[@liu2025opt2skill]]
  gets *dynamic feasibility by construction* from trajectory optimization; [[@xie2026grail]] gets *scale and
  diversity* from generative priors and enforces plausibility only post hoc via optimization losses plus a
  discard filter. Same tension as [[motion-imitation]] §Tension, one level up.
- Does anything in the CLF/ROM line extend to contact-rich whole-body tasks, where the "reduced order model"
  would have to include the manipulated object? Open — not something otto currently has a note on.
