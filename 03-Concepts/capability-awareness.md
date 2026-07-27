---
type: concept
tags: [navigation, control, open-question]
aliases: [capability-awareness, capability-aware navigation, learned capability boundary]
created: 2026-07-06
modified: 2026-07-07
---

# Capability-awareness

> [!note] Stub / research thesis — expand into your own words. This is the candidate contribution of [[capability-aware-navigation]].

## Definition
A navigation layer that respects the **learned low-level controller's emergent capability boundary** — the true feasible-command manifold of the trained policy — rather than an analytical reduced-order model's *assumed* boundary. Analytical ROMs (LIP/H-LIP) cannot represent what a learned controller can actually do, so a nav policy planning against the analytical model is either over-conservative or commands infeasible velocities.

## The mechanism under investigation
Repurpose the LLC's own CLF Lyapunov value $V_t=\eta^\top P\eta$ (from [[@li2025clf|CLF-RL]] training) as a real-time **comfort signal**: penalize the nav policy for commands that drive the LLC into high-$V$, out-of-distribution regimes. See [[control-lyapunov-function]].

## The ROM–reality gap: correct vs. bypass
The premise — an analytical ROM misrepresents the real (learned) system — is the *same* one my
earlier work answers by **correcting** the ROM instead of bypassing it. Three answers to one gap:
- **Correct with a learned tube:** bound the tracking error around the ROM plan — [[dynamic-tube]], [[@compton2025dynamic|DTMPC]]. See [[tracking-error-bound]].
- **Correct with a learned margin:** robustify the ROM-CBF for the full model — [[@compton2025learning|predictive CBFs]].
- **Bypass the ROM (this thesis):** discard the analytical model; use the learned LLC's own CLF value $V_t$ as the feasibility certificate.

## Distinguish from adjacent ideas
- **FocusNav's SASG** ([[@zhang2026focusnav]]) gates *perception* on a heuristic stability metric — this proposal penalizes *commands* on the LLC's *certified* Lyapunov value. Same intuition, different object, different guarantees.
- **Learned forward-dynamics models** ([[@roth2025learned]]) learn a capability/traversability model to plan against — a model-predictive route to the same "know what the platform can do" goal, vs. this reward-regularizer route.

## Grounding
- [[@li2025clf]] — source of $V_t$. · [[@roth2025learned]] — learned capability model (contrast). · [[@zhang2026focusnav]] — SASG (contrast).
- **External competence-aware precedent:** [[@pokhrel2024cahsor|CAHSOR]] — literally *competence-aware* navigation that trades performance for stability (**−62% instability for −8.6% speed**) via a learned SE(3) model. The closest external analogue to the $V_t$-comfort tradeoff, and arguably a prior claim on the "competence-aware navigation" framing — worth citing as such.
- **Learned-capability route (external, model-predictive):** [[@kahn2020badgr|BADGR]] · [[@kim2022forward]] · [[@jiang2023abstraction]] — learn what the platform can do / where it fails and plan against it, vs. this note's reward-regularizer route. See [[forward-dynamics-model]] and the [[informed-locomotion-planning]] map.

## Open tensions
> [!warning] ai-draft (weekly-review 2026-07-07) — four frictions the synthesis pass surfaced in
> this thesis. Written as prompts to sharpen, not settled claims; refine into your own words.

**1. Is $V_t$ even available at deployment?** The mechanism assumes the LLC exposes $V_t=\eta^\top P\eta$
at nav time. But [[@li2025clf|CLF-RL]] states the opposite about that value: *"the references and CLF
shaping are used only during training, so the deployed policy stays lightweight … CLFs enter as
reward-shaping, not a runtime QP constraint."* Computing $\eta^\top P\eta$ online needs the transverse
coordinates $\eta$ (error vs. a **reference trajectory**) and $P$ — precisely the reference-generation
machinery CLF-RL *discards* at deployment for lightweightness. So the thesis's central real-time signal
is not currently produced by the deployed controller. Resolution paths: reconstruct the reference online,
add a value head that regresses $V_t$, or distill $V_t$ into the LLC. **This needs an answer before the
"real-time comfort signal" framing holds.**

**2. Whose $V_t$? One frozen LLC vs. a multi-gait switch.** The project promises selecting speed/gait
(walk / run / stairs) over a *frozen, singular* CLF-RL LLC. But walking ([[@li2025clf]]), running
([[@olkin2025chasing]], 3.3 m/s), and terrain/stairs ([[@terrain2026consistent]]) are *different*
policies with different references, gaits, and CLFs — so "$V_t=\eta^\top P\eta$" is ambiguous: **which
$P$?** Over one velocity-tracking LLC, "gait selection" reduces to velocity selection (run emerges from
high $v_x$), a weaker claim than gait arbitration. And [[@zhang2026focusnav]]'s own intro indicts this
architecture: end-to-end methods *"emit velocity commands to a fixed low-level locomotion controller …
[which] can't support agile gait adjustments."* Decide whether the capability boundary is **one LLC's
velocity envelope** or a **switch across several CLF-RL controllers** (hence several $V_t$'s) — it
reshapes the whole formulation.

**3. Hard certificate vs. soft cost — and the quiet ARCHER→G1 safety downgrade.** The project stacks a
*hard* forward-invariance safety filter ([[@bena2025geometry|Poisson CBF-MPC]]) yet treats
capability-awareness as a *soft* reward regularizer. Zoom out and the whole portfolio's safety story has
migrated: the hopper line was **provable** — [[@cohen2025safety]] establishes RoM→FoM transfer,
[[@compton2025learning]] literally *"prove[s] this guarantees safety in a layered implementation."* The
G1 line drops the certificate — [[@terrain2026consistent]] / [[@olkin2026chasing]] wrap a CBF
*collision-avoidance* filter around a learned policy **whose tracking error is never bounded**. Two open
questions: (a) recover the RoM→FoM guarantee on the learned G1 policy, or consciously accept **empirical**
safety? (b) why is collision safety a certificate but capability/comfort merely a reward? This is the
hard-constraint-vs-learned-cost spine — its home is the [[informed-locomotion-planning]] map.

**4. SE(2) command interface vs. a humanoid running at 3.3 m/s.** [[@pokhrel2024cahsor|CAHSOR]] argues
SE(2) *"may not hold at high speeds … rollover … lateral sliding … vibration."* Yet [[@roth2025learned]],
[[@terrain2026consistent]], and [[@olkin2026chasing]] all commit to an **SE(2) velocity interface** on a
G1 running at 3.3 m/s (2 m/s while dodging obstacles) — exactly CAHSOR's "high-speed regime where SE(2)
breaks." Does the comfort signal $V_t$ need **SE(3) content** (the humanoid analogues of rollover/slip)
that an SE(2) command interface hides?

> [!warning] 5. A generative controller as architectural rival — on your exact robot (weekly-review 2026-07-26, ai-draft)
> [[@wang2026motionbricks|MotionBricks]] deploys a *generative* motion model with modular "smart primitives"
> as its command interface **directly on the Unitree G1** — a wholesale alternative to this project's stack
> (mid-level nav policy → **SE(2)** velocity → *frozen* CLF-RL LLC). Its interface is generative primitives, not
> a velocity command, and its "controller" is one large learned motion model rather than a certified LLC. It
> compounds tension **#2** (*whose* controller / which $V_t$?) and **#4** (is SE(2) rich enough?). And
> [[@cheng2024navila|NaVILA]] is a third interface data point — it commands the locomotion policy in **language**
> ("move forward 75cm"), not SE(2) either. Open: what do the primitive / language interfaces express that an
> SE(2) command can't — and does that moot the $V_t$-comfort signal, or *motivate* a richer one?

## See also
[[control-lyapunov-function]] · [[rl-for-legged-locomotion]] · [[traversability-estimation]] · [[forward-dynamics-model]] · [[informed-locomotion-planning]] · [[capability-aware-navigation]]
