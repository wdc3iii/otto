---
type: concept
tags: [rl, method, to-revisit]
aliases: [Privileged information, privileged observation, asymmetric actor-critic, informed POMDP]
created: 2026-07-29
modified: 2026-07-29
---

# Privileged information

> [!note] AI-drafted base, created 2026-07-29 alongside the ingest of [[auxiliary-prediction-heads]].
> Refine or reject.

## Definition
Information available **at training time only** — ground-truth state, a noiseless heightmap, a full
occupancy map, contact forces — used to train a policy that must run without it. The discipline is
about *where* it is allowed to enter, because different entry points have different consequences for
the learned policy.

## Intuition / why it matters
There are three distinct levers, and conflating them makes results uninterpretable:

1. **Into the critic** (asymmetric actor-critic). The policy gradient stays **unbiased** —
   [[@ebi2026informed]] shows this holds for arbitrary state-dependent privileged signals, not just
   full state, and gives criteria for picking informative ones. This is the "free" lever.
2. **Into a teacher, then distilled** (privileged training → student). The standard legged recipe:
   [[@miki2022learning]] trains a teacher on privileged terrain and distils into a student whose belief
   GRU *reconstructs* the privileged signal it cannot cleanly see.
3. **Into an auxiliary target on the actor's trunk** ([[auxiliary-task-learning]]). This
   **deliberately biases the actor's representation** — that is the entire point, but it is not the
   same as (1) and must not be reported as though it were.

[[@lambrechts2024informed]] gives the formal frame: an *informed POMDP* has training-time information
$i$ such that the observation is conditionally independent of the state given $i$, with an objective
that uses $i$ to learn a **sufficient statistic of the history**. The licence it grants is precise —
the aux *target* may be privileged so long as the policy *input* is not.

## Grounding
- **Unbiasedness in the critic:** [[@ebi2026informed]] (Informed Asymmetric Actor-Critic — carefully
  chosen partial signals match or beat full-state asymmetric baselines).
- **Theory of training-time-only information:** [[@lambrechts2024informed]] (Informed POMDP).
- **Legged practice — reconstruct-the-privileged-signal:** [[@miki2022learning]] (noiseless height
  samples + contacts/forces/friction from a 2-layer belief GRU, loss $\mathcal{L}_{bc} + 0.5\,
  \mathcal{L}_{re}$) · [[@ji2022concurrent]] · [[@nahrendra2023dreamwaq]].
- **In your own stack:** the privileged wavefront/occupancy map already sits in the nav policy's
  **critic** — see [[auxiliary-prediction-heads]], which is explicit that adding an actor-side aux head
  is a different lever from that existing asymmetry.

## Related
- [[auxiliary-task-learning]] — lever (3).
- [[belief-state]] — what "sufficient statistic of the history" means operationally.
- [[state-estimation]] · [[sim-to-real-transfer]] · [[traversability-estimation]]

## Open questions
- Which privileged signals are *worth* using? [[@ebi2026informed]] offers two selection criteria — do
  they pick out the same signals a decodability probe would?
- When a target is both privileged **and** already reachable from the observation history, is the aux
  head doing anything a longer BPTT window wouldn't?
