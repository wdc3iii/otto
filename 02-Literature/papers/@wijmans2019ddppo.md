---
type: paper
citekey: wijmans2019ddppo
tags: [rl, navigation, method]
aliases: [DD-PPO]
created: 2026-07-06
modified: 2026-07-06
authors:
  - Erik Wijmans
  - Abhishek Kadian
  - Ari Morcos
  - Stefan Lee
  - Irfan Essa
  - Devi Parikh
  - Manolis Savva
  - Dhruv Batra
year: 2019
venue: ICLR 2020
doi:
arxiv: '1911.00357'
url: https://arxiv.org/abs/1911.00357
pdf: attachments/@wijmans2019ddppo.pdf
zotero:
status: read
mine: false
---

# DD-PPO: Learning Near-Perfect PointGoal Navigators from 2.5 Billion Frames

> [!info] Wijmans, Kadian, Morcos, Lee, Essa, Parikh, Savva & Batra · 2019 · ICLR 2020

## TL;DR
A decentralized, synchronous variant of PPO that removes the parameter server and instead synchronizes gradients across GPU workers via AllReduce (PyTorch DistributedDataParallel). It scales near-linearly to hundreds of GPUs, letting the authors train a PointGoal navigation agent for 2.5 billion frames (~80 years of experience, <3 days wall-clock on 64 GPUs) and essentially *solve* the task — near-shortest-path navigation in unseen indoor scenes from RGB-D + GPS+Compass, without any map.

## Problem
The dominant distributed-RL paradigm — a central parameter server feeding thousands of asynchronous CPU rollout workers — is a poor fit for embodied AI, where each worker needs a GPU (photorealistic 3D sim + deep ResNet policy) and worker counts are small (2^5–2^8 vs. 2^12–2^15 for Atari). Asynchrony also introduces staleness and opaque failure modes. Separately, prior work (Mishkin 2019, Savva 2019) had only trained PointGoal agents to ~5–75M steps and left open the scientific question of what the *limits of learnability* are for map-free PointGoal navigation.

## Method
- **DD-PPO.** Every worker holds a full copy of the model and alternates between (1) collecting a rollout in its own simulator instance and (2) computing PPO gradients. Workers then AllReduce (mean) their gradients and take an identical optimizer step — synchronous, decentralized (no parameter server), conceptually just "data-parallel supervised training" adapted to on-policy RL. All workers run identical code.
- **Preemption threshold.** To defeat stragglers from environments that vary wildly in sim time, once *p%* of workers finish collecting their rollout, the rest are forced to stop early. They find **p = 60%** works well; losses are weighted equally across workers and each is guaranteed a minimum of 1/4 of max steps so every environment contributes.
- **PointGoal agent architecture.** Visual encoder (ResNet50 or SE-ResNeXt) with a first-layer 2×2 AvgPool and halved channel counts; **all BatchNorm replaced by GroupNorm** to handle the highly-correlated inputs of on-policy RL. Policy is a **2-layer LSTM, 512-d hidden** (best model uses 1024-d), taking the previous action, the goal-vector relative to current pose, and the visual embedding; outputs an action softmax + value estimate. Actions: `stop`, `move_forward` (0.25m), `turn_left`/`turn_right` (10°). 256×256 images; Depth found best.
- **Training config (the reproducible part).** PPO + GAE, γ = 0.99, GAE τ = 0.95. Each worker runs 4 environments in parallel and collects up to 128 frames, then does 2 PPO epochs × 2 mini-batches. Adam, lr = 2.5e-4. **Advantages are NOT normalized** (they found this causes instability). 64 workers on 64 GPUs. Reward: terminal r_T = 2.5·SPL, shaped r_t = −Δ(geodesic distance to goal) − 0.01. Simulator: Habitat-Sim; scenes from Gibson + Matterport3D.

## Key results
- **Scaling:** 107× speedup on 128 GPUs over serial; near-linear under both homogeneous and heterogeneous workloads for preemption thresholds >50% (196× at 256 GPUs, 7.3× at 8 GPUs). p = 60–80% recovers near-identical scaling to the homogeneous case.
- **Solving PointGoalNav:** Best agent (SE-ResNeXt101 + 1024-d LSTM, Gibson-2+) reaches **SPL 0.969 val / 0.948 test**, within **3–5% of the shortest-path oracle** and failing only ~1/1000 val episodes — SOTA on Habitat Challenge 2019 RGB-D. Performance keeps improving out to 1B+ steps (prior work saturated 1–2 orders of magnitude too early).
- **Power-law compute curve:** 90% of peak SPL is reached by ~100M steps (<1 day on 8 GPUs); the last few points of SPL cost the bulk of the 2.5B-frame budget.
- **RGB (no depth):** improves from Savva 2019's ~0.47 test SPL to **0.920 test SPL / 99.1% success**.
- **Blind agent** (GPS+Compass only, no vision) does fine on short-range but collapses on 20–25m episodes (SPL 0.3 vs 0.95) — evidence the RGB-D agent leans hard on depth for long-range and on floor-plan regularities for short-range.
- **No GPS+Compass** (RGB only): only **0.15 SPL** even at 2.5B steps — an open frontier.
- **Transfer:** PointGoalNav-pretrained visual encoders beat ImageNet-pretrained CNNs on Flee/Exploration tasks; framed as "ImageNet-pretraining for embodied AI." A frozen PointGoalNav policy can even be driven as a **differentiable neural controller** by a lightweight high-level LSTM planner that emits goal-coordinates, backprop-through the controller.

## Limitations / open questions
- Map-free navigation from **RGB alone, without GPS+Compass**, remains essentially unsolved (0.15 SPL).
- Near-perfect SPL likely exploits statistical regularities of real indoor floor-plans; an adversarially-designed map could break the "no wrong turns" behavior. Not a guarantee of optimality in arbitrary environments.
- Only demonstrated on-policy (PPO); off-policy adaptation is conjectured, not shown.
- Pure sim (Habitat) — no sim-to-real deployment in this paper.

## Concepts
- [[recurrent-navigation-policy]]
- [[mapless-navigation]]

## My notes
Kept as a **config/architecture reference**, not a domain competitor. This is, as far as I can tell, the most completely-specified published recurrent-PPO setup in embodied AI, which makes it the natural cross-check for my recurrent-PPO configuration in `rsl_rl` for the mid-level recurrent navigation policy:

- **Recurrent policy shape:** 2-layer LSTM, 512-d (1024-d for the big model) sitting on top of a visual encoder, consuming previous action + goal-relative vector + embedding. A clean template for a mid-level policy that takes a relative goal and a perception embedding.
- **On-policy RL normalization gotchas worth porting:** (1) **GroupNorm, not BatchNorm** — correlated on-policy batches make BN pathological; (2) they explicitly **do not normalize advantages** and report instability when they do. Both are cheap to check against the rsl_rl defaults.
- **PPO hyperparameters** are all here (γ=0.99, GAE τ=0.95, lr 2.5e-4 Adam, 2 epochs × 2 minibatches, 128-step rollouts × 4 envs/worker) — a sane starting point / sanity baseline for the recurrent config.
- **DD-PPO itself** (AllReduce-synchronized, no parameter server) is the same distributed pattern rsl_rl / IsaacGym-style training already relies on, so the scaling story is familiar territory rather than novel to adopt.
- The **"differentiable neural controller"** framing — freeze a goal-reaching low-level policy and train a high-level LSTM planner to emit goal-coordinates, backprop through the frozen controller — is a concrete instance of the [[hierarchical-control]] decomposition I care about, in a purely learned setting. Contrast with my classical planner + learned locomotion split.
- Caveat for my use: this is a wheeled-abstraction point agent in sim (discrete 0.25m / 10° actions, no dynamics, no map, no hardware). Relevant for policy *architecture and training recipe*, not for locomotion dynamics or sim-to-real.

## Source
arXiv:1911.00357 (v2, 2020-01-20) · https://arxiv.org/abs/1911.00357 · ICLR 2020. Code: github.com/facebookresearch/habitat-api. PDF: `attachments/@wijmans2019ddppo.pdf`.
