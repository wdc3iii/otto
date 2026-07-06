---
type: concept
tags: [navigation, control, open-question]
aliases: [capability-awareness, capability-aware navigation, learned capability boundary]
created: 2026-07-06
modified: 2026-07-06
---

# Capability-awareness

> [!note] Stub / research thesis — expand into your own words. This is the candidate contribution of [[capability-aware-navigation]].

## Definition
A navigation layer that respects the **learned low-level controller's emergent capability boundary** — the true feasible-command manifold of the trained policy — rather than an analytical reduced-order model's *assumed* boundary. Analytical ROMs (LIP/H-LIP) cannot represent what a learned controller can actually do, so a nav policy planning against the analytical model is either over-conservative or commands infeasible velocities.

## The mechanism under investigation
Repurpose the LLC's own CLF Lyapunov value $V_t=\eta^\top P\eta$ (from [[@li2025clf|CLF-RL]] training) as a real-time **comfort signal**: penalize the nav policy for commands that drive the LLC into high-$V$, out-of-distribution regimes. See [[control-lyapunov-function]].

## Distinguish from adjacent ideas
- **FocusNav's SASG** ([[@zhang2026focusnav]]) gates *perception* on a heuristic stability metric — this proposal penalizes *commands* on the LLC's *certified* Lyapunov value. Same intuition, different object, different guarantees.
- **Learned forward-dynamics models** ([[@roth2025learned]]) learn a capability/traversability model to plan against — a model-predictive route to the same "know what the platform can do" goal, vs. this reward-regularizer route.

## Grounding
- [[@li2025clf]] — source of $V_t$. · [[@roth2025learned]] — learned capability model (contrast). · [[@zhang2026focusnav]] — SASG (contrast).

## See also
[[control-lyapunov-function]] · [[rl-for-legged-locomotion]] · [[traversability-estimation]] · [[capability-aware-navigation]]
