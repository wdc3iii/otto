---
type: concept
tags: [control, planning, to-revisit]
aliases: [reduced order model, RoM, planning model]
created: 2026-07-05
modified: 2026-07-05
---

# Reduced-order model

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
A low-dimensional model capturing the states relevant to a task (e.g. center-of-mass / kinematic configuration for safety and navigation) while abstracting away full-order dynamics. Design (planning, CBF/CLF synthesis, MPC) happens on the RoM; a lower-level controller tracks the resulting behavior on the full-order model (FoM).

## Intuition / why it matters
RoMs make otherwise intractable design tractable — you reason in a small space and lean on a tracking layer to realize it. The catch is the **RoM↔FoM gap**: guarantees only transfer if tracking error is bounded and accounted for (via a [[tracking-error-bound]], simulation functions, or a robustifying margin).

## Grounding
- [[@cohen2025safety]] · [[@compton2025learning]] — formal RoM→FoM safety transfer and its learned robustification.
- [[@compton2025dynamic]] — the planning model whose tracking tube is learned.
- [[@dai2025walk]] — LIP-style reduced-order stepping planner.

## Related
- [[hierarchical-control]] · [[tracking-error-bound]] · [[control-barrier-function]]

## Open questions
- How to choose the RoM so the FoM gap is both small and cheaply bounded?
