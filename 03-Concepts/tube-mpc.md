---
type: concept
tags: [control, planning, to-revisit]
aliases: [tube MPC, tube model predictive control, robust tube MPC]
created: 2026-07-05
modified: 2026-07-05
---

# Tube MPC

> [!todo] Concept stub — auto-created while ingesting [[@compton2025dynamic]]. Replace with your own words, then drop the `to-revisit` tag.

Robust MPC that plans a nominal trajectory and buffers it by an error "tube" so the true (perturbed) trajectory stays safe. Classic variants fix the tube to a worst-case width.

## Grounding
- [[@compton2025dynamic]] — motivates *dynamic* (action-dependent) tubes over fixed ones.
- [[@langson2004]] · [[@lopez2019]] · [[@fan2020]]

## Related
- [[dynamic-tube]] · [[tracking-error-bound]]

## Open questions
