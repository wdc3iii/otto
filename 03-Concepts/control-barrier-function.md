---
type: concept
tags: [control, to-revisit]
aliases: [control barrier function, CBF, CBFs, ISSf-CBF]
created: 2026-07-05
modified: 2026-07-05
---

# Control barrier function

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
A control barrier function is a scalar `h(x)` whose zero-superlevel set `{x : h(x) ≥ 0}` is the safe set. That set is rendered **forward-invariant** by any input satisfying the pointwise condition `ḣ(x,u) ≥ -α(h(x))` for a class-𝒦 function α. Since the condition is affine in the input for control-affine systems, a **QP safety filter** can minimally modify any nominal controller to guarantee safety.

## Intuition / why it matters
The safety analogue of a control Lyapunov function: instead of certifying convergence, it certifies *never leaving* the safe set, converting an infinite-horizon "stay safe forever" requirement into one instantaneous inequality. **ISSf-CBFs** add a margin so safety is robust to bounded disturbance / model error — essential when a guarantee proven on a reduced-order model must survive tracking error on the full system.

## Grounding
- [[@compton2025learning]] · [[@cohen2025safety]] — your RoM-CBF synthesis and predictive/learned robustification.
- [[@molnar2022model]] · [[@cohen2024safety]] · [[@wabersich2023data]] — model-free / ROM CBFs and data-driven safety filters.
- [[@compton2025dynamic]] — ISSf-CBF safety in the tube-MPC setting.
- [[@bena2025geometry]] · [[@yang2026safesage]] — perception-driven CBFs synthesized from occupancy via a [[poisson-safety-function]] (MPC+CBF filter; Laplace-modulated for [[social-navigation|semantic/social safety]]).

## Related
- [[tracking-error-bound]] · [[reduced-order-model]] · [[tube-mpc]]

## Open questions
- Constructive CBF synthesis for high-dimensional systems remains largely open — your ROM-based approach is one answer.
