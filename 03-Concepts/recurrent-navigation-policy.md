---
type: concept
tags: [navigation, rl, method]
aliases: [recurrent navigation policy, implicit mapping, memory-based navigation]
created: 2026-07-06
modified: 2026-07-29
---

# Recurrent navigation policy

> [!note] Stub — expand when revisited. This is the [[capability-aware-navigation]] mid-level architecture pattern.

## Definition
A recurrent (LSTM/GRU/SRU) policy that sits **over a frozen locomotion controller**, consumes perception + goal + proprioception, and emits velocity commands — doing mapping/planning **implicitly in its hidden state** rather than via an explicit metric map. Trained end-to-end (typically PPO). The recurrent state is where long-horizon spatial memory lives.

## Why it matters
The learned alternative to explicit SLAM+planner navigation, and the middle tier of the humanoid stack. Key open issue: vanilla RNNs encode temporal order but **not egocentric spatial registration** — the gap [[@yang2025spatially|SRU]] targets. Belief-state conditioning ([[@lee2024learning]] feeds the LLC's hidden state to the HLC) and recurrent belief estimation ([[@hoeller2021learning]]) are recurring design moves.

## Grounding
- [[@yang2025spatially]] — SRU (spatial memory). · [[@hoeller2021learning]] — VAE+LSTM predecessor. · [[@lee2024learning]] — belief-state-as-HLC-input HRL. · [[@wijmans2019ddppo]] — recurrent-PPO recipe at scale. · [[@haro2026path]] — path-conditioned recurrent local planner.
- **What the recurrent state actually holds, and how to make it hold more** (*added 2026-07-29*): see [[belief-state]] and [[auxiliary-task-learning]]. Key results — [[@lambrechts2022recurrent]] (do hidden states approximate beliefs?) · [[@pasukonis2022evaluating]] (reward alone under-trains memory) · [[@mirowski2017learning]] (supervising *from the recurrent output* beat supervising from the encoder) · [[@ye2021auxiliary]] (one belief module per aux task, attention-fused, past ~2 tasks). Design proposal for your own nav policy: [[auxiliary-prediction-heads]].

## See also
[[hierarchical-control]] · [[mapless-navigation]] · [[sim-to-real-transfer]] · [[capability-aware-navigation]]
