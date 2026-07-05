---
type: concept
tags: [control, planning, to-revisit]
aliases: [tube MPC, tube model predictive control, robust tube MPC]
created: 2026-07-05
modified: 2026-07-05
---

# Tube MPC

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
A robust MPC that plans a nominal trajectory and surrounds it with an error **tube** guaranteed to contain the true (disturbed / model-mismatched) trajectory; constraints are tightened by the tube so the realized trajectory stays feasible and safe. Classic formulations fix the tube to a worst-case robust invariant set.

## Intuition / why it matters
Decouples nominal planning from disturbance rejection: plan for the nominal model, then buffer by the tube. Tube size is the performance-vs-robustness knob — a fixed worst-case tube is safe but overly conservative, which is exactly what a [[dynamic-tube]] addresses.

## Grounding
- [[@langson2004robust]] — the original tube-MPC formulation.
- [[@lopez2019dynamic]] · [[@fan2020deep]] — nonlinear / learned-tube variants.
- [[@compton2025dynamic]] — your dynamic (action-dependent) tube MPC.

## Related
- [[dynamic-tube]] · [[tracking-error-bound]]

## Open questions
- Tight, feasible tubes for nonlinear systems without hand-designed invariant sets.
