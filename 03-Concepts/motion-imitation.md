---
type: concept
tags: [rl, imitation, to-revisit]
aliases: [Motion imitation, physics-based character control, reference motion tracking]
created: 2026-07-26
modified: 2026-07-29
---

# Motion imitation

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
Learning **physics-based controllers that reproduce reference motion** (mocap or human video) via RL — spanning single-clip tracking, adversarial motion priors, reusable skill latents, and unified large-scale controllers. The through-line: use data to specify *what natural motion looks like* instead of hand-engineering it into a reward.

## Intuition / why it matters
This lineage (character-animation origins → humanoid robotics) is now the dominant recipe for **versatile whole-body humanoid skills**, and it lands directly on my hardware: [[@liao2025beyondmimic|BeyondMimic]] runs composed skills on a real humanoid, and [[@wang2026motionbricks|MotionBricks]] deploys on the Unitree G1. The open tension with my line: imitation gives *natural, versatile* motion but not *certifiable stability* — where [[rl-for-legged-locomotion|CLF-guided RL]] pushes back.

## Grounding
- Ancestor: [[@peng2018deepmimic]] (DeepMimic — example-guided RL, single-clip tracking).
- Adversarial priors: [[@peng2021amp]] (AMP), [[@peng2022ase]] (ASE — reusable skill embeddings).
- Unified / large-scale: [[@luo2023perpetual]] (PHC), [[@luo2024universal]] (PULSE), [[@tessler2024maskedmimic]] (MaskedMimic), [[@wang2026motionbricks]] (MotionBricks).
- On real humanoids: [[@liao2025beyondmimic]] (guided diffusion over tracked primitives).
- Generated references: [[@xie2026grail]] (GRAIL — tracks 4D human–object interaction reconstructed from VFM-generated video, via an adaptor on a frozen pretrained controller; extends the lineage to [[loco-manipulation]]).

## Related
- [[rl-for-legged-locomotion]] · [[diffusion-model]]

## Open questions
- **Sim-to-real** for extremely dynamic skills on real humanoid hardware.

> [!warning] Tension — structure-for-certification vs. scale-for-versatility (weekly-review 2026-07-26, ai-draft)
> Two opposing bets on humanoid whole-body control now sit side by side in otto:
> - **My line** — *inject structure* (ROM/CLF/references) into RL: [[@olkin2026stability]] **proves** CLF-guided RL stable, and [[@terrain2026consistent]] exposes a planner-compatible $SE(2)$ interface. Certifiable, but curated behaviors.
> - **The imitation-scaling line** — [[@liao2025beyondmimic|BeyondMimic]], [[@tessler2024maskedmimic|MaskedMimic]], [[@luo2023perpetual|PHC]], [[@wang2026motionbricks|MotionBricks]] get *versatile* whole-body skills by scaling data-driven imitation, with **no stability certificate**.
>
> Open: does the CLF-RL stability result say anything *about* — or *against* — the imitation route, or are these just incompatible bets? [[@liao2025beyondmimic|BeyondMimic]] straddles both (guided diffusion over tracked primitives, run on hardware), so it's the natural place to probe whether structure and scale can be *combined* rather than chosen between.
