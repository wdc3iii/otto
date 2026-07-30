---
type: concept
tags: [rl, open-question, to-revisit]
aliases: [Belief state, belief representation, hidden state, sufficient statistic of history]
created: 2026-07-29
modified: 2026-07-29
---

# Belief state

> [!note] AI-drafted base, created 2026-07-29 alongside the ingest of [[auxiliary-prediction-heads]].
> Refine or reject.

## Definition
In a POMDP, the **posterior over states given the history** — and, in practice, whatever a recurrent
policy's hidden state actually manages to encode of it. The formal object is a *sufficient statistic of
the history*; the empirical object is a 128-unit GRU state that may or may not approximate one.

## Intuition / why it matters
The gap between those two is where the interesting failures live. A recurrent policy is *architecturally*
capable of carrying history, but the only pressure to do so is the reward gradient through a truncated
BPTT window — and that pressure is weak:

- [[@pasukonis2022evaluating|Memory Maze]] isolates long-term memory and finds model-free agents with
  truncated BPTT plateau far below human on large mazes, while reconstruction-based world models do
  better. **Reward alone under-trains memory.**
- [[@lambrechts2022recurrent]] asks the question directly — how well *do* RNN hidden states in
  model-free RL approximate belief states? That is exactly what a post-recurrent decodability probe
  measures.
- [[@yang2025spatially]] locates a sharper failure: LSTM/GRU/S4/Mamba all handle *temporal* recall but
  fail at **spatial memorisation across viewpoint change**. That's an inductive-bias claim, and it
  implies the fix might be the cell, not the supervision.

Three routes to a better belief state, which is the real design fork:
1. **Supervise it** with privileged reconstruction targets ([[auxiliary-task-learning]],
   [[privileged-information]], [[@miki2022learning]]).
2. **Model it generatively** — [[@igl2018deep]] structures the recurrent update as approximate belief
   inference with an ELBO; [[@guo2018neural]] compares CPC / CPC|Action / PBL predictive objectives and
   analyses *why* action-conditional prediction beats plain contrastive for belief content.
3. **Change the cell** so the right thing is easy to represent — [[@yang2025spatially]]'s spatial
   "star operation," with no auxiliary losses at all.

## Grounding
- **Is the belief in there?** [[@lambrechts2022recurrent]] (empirical study) ·
  [[@pasukonis2022evaluating]] (benchmark + offline probing protocol).
- **Formal target:** [[@lambrechts2024informed]] (sufficient statistic of the history, learned using
  training-time information).
- **Generative / model-based routes:** [[@igl2018deep]] (DVRL) · [[@guo2018neural]] (PBL) ·
  [[world-model]].
- **Supervised route, on hardware:** [[@miki2022learning]] (2-layer belief GRU + attention gate on
  exteroception, decoder reconstructing privileged state).
- **Architectural route:** [[@yang2025spatially]] (SRU) · [[recurrent-navigation-policy]].
- **Where attachment point was shown to matter:** [[@mirowski2017learning]] (depth-from-LSTM beat
  depth-from-conv) · [[@ye2021auxiliary]] (one belief module per aux task, attention-fused).

## Related
- [[recurrent-navigation-policy]] — the architecture that carries it.
- [[auxiliary-task-learning]] · [[privileged-information]] · [[world-model]] · [[state-estimation]]

## Open questions
- **Supervision vs. inductive bias** — the central unresolved fork. These are parallel arms, not
  sequential steps; see [[auxiliary-prediction-heads]] §5.
- What does a decodability probe at the post-recurrent site actually license you to conclude? If a
  target is decodable, is the belief "there," or merely linearly recoverable in a way the policy
  doesn't use?
- **BPTT horizon as a hard ceiling.** A memory target longer than the BPTT window is partly
  unlearnable by construction — so a negative result can be an artefact of the window rather than
  evidence about memory. (Your §4.4 makes this point about a 36-step / 7.2 s window.)
