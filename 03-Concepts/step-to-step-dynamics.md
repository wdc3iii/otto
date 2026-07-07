---
type: concept
tags: [control, locomotion, to-revisit]
aliases: [step-to-step dynamics, S2S, H-LIP, hybrid-LIP, step-to-step]
created: 2026-07-06
modified: 2026-07-07
---

# Step-to-step (S2S) dynamics

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
The **discrete map from one step to the next** for a walking system: given the pre-impact state and a chosen foot placement, S2S dynamics predict the state at the start of the following step. For underactuated bipeds this is the natural control abstraction — you cannot fully control continuous dynamics within a step, but you *can* steer the discrete step-to-step evolution through **foot placement**. The **Hybrid-LIP (H-LIP)** is the canonical reduced-order instance: a linear-inverted-pendulum S2S model whose stepping controller stabilizes orbits and can be composed with a tracking layer.

## Intuition / why it matters
S2S is the [[reduced-order-model]] specialized to *stepping*: the planning variable is where to step, and stability is an orbital / discrete-time property rather than a continuous one. It is the substrate the CLF-guided RL and ROM-stepping-planner lines build on (references come from an S2S/H-LIP plan), so it deserves its own address rather than being folded under the generic RoM note.

## Grounding
- [[@xiong2019orbit]] — orbit characterization, stabilization, and composition for underactuated bipedal walking (the H-LIP orbit framework).
- [[@xiongnd3d]] — 3D underactuated bipedal walking via H-LIP stepping.
- [[@xiongndglobal]] — global-position control through the H-LIP stepping abstraction.
- [[@dai2021bipedal]] — bipedal walking on constrained footholds via momentum / step control.
- [[@dai2023data]] — data-driven adaptation of the S2S map for robust bipedal locomotion.
- [[@xiong2022underactuated]] — the H-LIP gait-synthesis + stepping-stabilization paper (S2S dynamics → provable stepping control on Cassie); the anchor of the H-LIP line.
- [[@dai2022bipedal]] — per-step (discrete-impact) angular-momentum regulation on constrained footholds via an underactuated-LIP model.
- [[@khadiv2020walking]] — selects next-step location **and** timing per control cycle with a viability guarantee (LIP-based).

## Related
[[reduced-order-model]] · [[hierarchical-control]] · [[tracking-error-bound]] · [[contact-implicit-mpc]] — the *opposite pole* of contact handling: S2S **prescribes** the contact sequence/timing (periodic orbit) and chooses only foot *placement* on a linear reduced model, whereas contact-implicit MPC lets the optimizer **discover** contact timing/location on the full model.

## Open questions
- How does S2S stepping compose with a learned [[forward-dynamics-model]] at the navigation layer — plan footholds on S2S, plan routes on the FDM?
