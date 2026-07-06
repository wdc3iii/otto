---
type: concept
tags: [control, to-revisit]
aliases: [control Lyapunov function, CLF, CLFs, CLF-QP]
created: 2026-07-06
modified: 2026-07-06
---

# Control Lyapunov function

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
A control Lyapunov function is a positive-definite scalar `V(x)` for which some admissible input can always drive it downhill — i.e. `inf_u V̇(x,u) ≤ -α(V(x))` for a class-𝒦 function α — certifying **asymptotic (or exponential) stabilizability** of the origin. For control-affine systems the condition `L_f V + L_g V·u ≤ -α(V)` is affine in `u`, so a **CLF-QP** can synthesize a minimum-norm stabilizing input pointwise.

## Intuition / why it matters
The stability dual of a [[control-barrier-function]]: a CBF certifies *never leaving* the safe set; a CLF certifies *converging* to the goal, both by turning an infinite-horizon requirement into one pointwise inequality. That inequality is also a natural, **model-grounded reward signal** — driving `V` down is a dense, certifiable objective — which is what the [[rl-for-legged-locomotion|CLF-guided RL]] line exploits in place of hand-tuned reward shaping.

## Grounding
- [[@olkin2026stability]] — stability theory for CLF-guided RL (the reward = decrease condition).
- [[@dai2025walk|PLANC]] · [[@li2025clf|CLF-RL]] — CLF rewards guiding locomotion policies.
- [[@huang2023efficient]] — CLF-reactive planning on undulating terrain.
- [[capability-awareness]] — repurposing the learned LLC's CLF value $V_t$ as a navigation-level comfort penalty (candidate contribution of [[capability-aware-navigation]]).

## Related
- [[control-barrier-function]] (safety sibling) · [[rl-for-legged-locomotion]] · [[reduced-order-model]]

## Open questions
- Constructive CLF synthesis for **underactuated / high-dimensional** systems is hard — reduced-order models and learning are two routes.
- What exactly does a CLF *reward* certify about the resulting **learned** closed loop? (see [[@olkin2026stability]]).
