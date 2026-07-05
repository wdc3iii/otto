---
type: concept
tags: [control, to-revisit]
aliases: [tracking error bound, tracking invariant, error bound]
created: 2026-07-05
modified: 2026-07-05
---

# Tracking-error bound

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
A guaranteed bound on the discrepancy between the full-order state (or its projection) and the reduced-order reference under the tracking controller — the "tracking invariant." Often a forward-invariant sublevel set of a Lyapunov/CLF (a fixed error ball); when no analytic Lyapunov function exists, a **learned or quantile** bound.

## Intuition / why it matters
This is the glue that lets RoM-level guarantees (safety, feasibility) hold on the FoM: buffer the plan by the error bound and you stay safe. Worst-case bounds are safe but conservative; **action-dependent / learned** bounds ([[dynamic-tube]]) tighten them by exploiting that some references are easier to track.

## Grounding
- [[@compton2025dynamic]] — learned, action-dependent bound (the dynamic tube).
- [[@csomayshanklin2022multi]] — multi-rate planning/control with CLF-based bounds.
- [[@cohen2025safety]] — simulation functions transferring error/safety RoM→FoM.

## Related
- [[reduced-order-model]] · [[tube-mpc]] · [[control-barrier-function]]

## Open questions
- Analytic (conservative, certified) vs learned (tight, statistical) bounds — how to get both tightness and hard guarantees?
