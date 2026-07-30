---
type: concept
tags: [rl, method, to-revisit]
aliases: [Auxiliary task, auxiliary loss, auxiliary head, aux task]
created: 2026-07-29
modified: 2026-07-29
---

# Auxiliary task learning

> [!note] AI-drafted base, created 2026-07-29 alongside the ingest of [[auxiliary-prediction-heads]].
> Grounded in the papers you assembled there — your own framing in that note is the authoritative
> version; this is the reusable distillation. Refine or reject.

## Definition
Adding a **supervised prediction head on a shared trunk**, trained jointly with the RL objective, so
that the representation is shaped by a dense signal the reward cannot supply. The policy input is
unchanged; only the *representation* is pushed. Total loss $= \mathcal{L}_{RL} + \sum_i \beta_i
\mathcal{L}^i_{aux}$.

## Intuition / why it matters
Reward is a scalar arriving late; an aux target is a rich vector arriving every frame. Where the two
diverge most is **memory**: a recurrent policy gets gradient pressure to remember only through the
BPTT window, and [[@pasukonis2022evaluating|Memory Maze]] is the evidence that reward alone
under-trains it. So the lever isn't "add more supervision" but *which* target, attached *where*:

- **Attachment point matters, empirically.** [[@mirowski2017learning]] found depth prediction from the
  **LSTM output** beat the same prediction from the conv output — the benefit came from forcing the
  *recurrent state* to carry geometry, not from shaping the encoder. Pre-trunk heads are encoder
  reconstruction; post-recurrent heads are memory supervision.
- **Target history-dependence matters more.** A target computable from the current frame can be
  satisfied without storing anything. The sharpest instrument is a target that is *only* satisfiable
  by remembering — which is why [[@ye2021auxiliary|coverage prediction]] was the single largest
  ablation contributor in ObjectNav, and why masking a target to the **currently invisible** region
  ([[occupancy-anticipation]]) converts a reconstruction task into a memory task.
- **It is not free.** Aux gradients change the effective step on shared parameters, and negative
  transfer is real — [[@du2018adapting]] gates each aux loss by the cosine similarity between its
  gradient and the main loss's. [[@lyle2021effect]] is the theory argument for choosing *few,
  well-aligned* targets rather than stacking heads.

## Grounding
- **Origins / canon:** [[@jaderberg2017reinforcement]] (UNREAL — aux tasks on a shared recurrent trunk,
  ~10× speedup) · [[@mirowski2017learning]] (depth + loop closure; classification > regression;
  post-LSTM > post-conv) · [[@shelhamer2017loss]].
- **The practical recipe:** [[@ye2020auxiliary]] — set each $\beta$ so the aux term is the same order of
  magnitude as the RL loss **at init** ($\beta \approx 0.1$–$0.4$), and **subsample** aux losses to
  10–20% of timesteps to bound cost. [[@ye2021auxiliary]] — beyond ~2 tasks, switch to one belief
  module per task fused by attention.
- **Legged / concurrent-with-PPO precedent:** [[@nahrendra2023dreamwaq]] (CENet — supervised velocity +
  VAE heads in the same graph as PPO) · [[@ji2022concurrent]] (state estimator trained alongside the
  policy) · [[@miki2022learning]] (belief GRU reconstructing noiseless height + privileged state at
  $0.5\times$ the main loss — but in **distillation**, competing with a BC loss, not a policy gradient).
- **Cheapest possible variant:** [[@ahmed2021self]] (temporal-order classification, no privileged
  information at all) — the near-free control arm.
- **Cautions:** [[@du2018adapting]] · [[@lyle2021effect]].
- **Encoder-side, for transfer:** [[@gordon2019splitnet]].

## Related
- [[belief-state]] — what a post-recurrent aux head is trying to shape.
- [[privileged-information]] — where the target is allowed to come from, and why that's a *different*
  lever from a privileged critic.
- [[occupancy-anticipation]] — the visibility-masking trick that makes a geometric target memory-bound.
- [[recurrent-navigation-policy]] · [[state-estimation]]

## Open questions
- **Is the deficit representational or architectural?** If a recurrent cell simply cannot align
  observations across ego-motion, no aux target fixes it — [[@yang2025spatially|SRU]] reports +23.5%
  over standard RNNs with **no auxiliary losses at all**. Aux supervision and a better cell are
  competing hypotheses that have to be run as parallel arms, not sequential steps.
- **Probe before training.** If a target is already linearly decodable from the trunk, an aux head on
  it should buy little. [[@lambrechts2022recurrent]] is the background for reading such a probe.
- Does the distillation→PPO transfer hold? Every strong legged precedent
  ([[@miki2022learning]]) puts the aux loss against a BC loss, not a policy gradient.
