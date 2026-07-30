---
type: paper
citekey: hoeller2021learning
tags: [navigation, rl, hardware]
aliases: []
created: 2026-07-06
modified: 2026-07-29
authors:
  - David Hoeller
  - Lorenz Wellhausen
  - Farbod Farshidian
  - Marco Hutter
year: 2021
venue: IEEE RA-L
doi:
arxiv: '2103.04351'
url: https://arxiv.org/abs/2103.04351
pdf: attachments/@hoeller2021learning.pdf
zotero:
status: read
mine: false
---

# Learning a State Representation and Navigation in Cluttered and Dynamic Environments

> [!info] Hoeller, Wellhausen, Farshidian, Hutter · 2021 · IEEE RA-L
> [!info]- otto authors: [[marco-hutter]]

## TL;DR
A two-stage learned local-navigation pipeline for a quadruped (ANYmal): an unsupervised state-representation module (VAE + LSTM) compresses a stream of noisy depth frames + camera trajectory into a compact latent belief state, and a small MLP policy trained with RL in simulation consumes that latent to reach a goal while avoiding static and dynamic obstacles — no explicit map. Decoupling representation from control makes the RL stage extremely sample-efficient (fully trained in simulation in ~12 minutes) and the learned latent is what bridges the reality gap for zero-extra-tuning sim-to-real.

## Problem
Local navigation among static *and* moving obstacles from onboard depth alone, without SLAM/occupancy grids or hand-engineered motion prediction. Classical model-based pipelines assume a mostly static world and get complicated/slow when forced to estimate and predict dynamic obstacle motion; end-to-end deep-RL-from-pixels is sample-hungry, hyperparameter-sensitive, and needs curricula. The goal is a task- and robot-agnostic module that fuses temporal depth into a control-ready state and enables reactive, foresightful obstacle avoidance that transfers to hardware.

## Method
Two decoupled components:
- **State representation (unsupervised).** A convolutional **VAE** encodes each depth frame to a 32-dim latent; the sequence of latents plus the camera's relative trajectory δψ is fed through a 2-layer **LSTM** (hidden dim 128) whose hidden state is mapped by MLPs to a Gaussian over the *next* latent. Trained by maximizing measured-latent log-likelihood + a KL term — effectively a non-linear Kalman-filter-like estimator: it "dreams" (dynamics update) when no measurement arrives and corrects on new frames. The VAE reconstruction target is a *filtered* depth image (dilation, hole-closing, bilateral filter, inspired by IP-Basic) so filtering is baked into the forward pass at no inference cost and helps close the sim-to-real depth gap. They compare this "world model" latent against a seq-to-seq encoder-decoder LSTM variant and a memoryless "reactive" VAE-only variant.
- **Policy (RL).** A simple MLP takes the belief state + goal and outputs base velocity commands (x, y, yaw) for a cuboid collision model (not the full robot), trained with **PPO** in NVIDIA Isaac Gym across procedurally randomized worlds (narrow corridors → open rooms, randomized furniture, moving obstacles up to 0.8 m/s). VAE is frozen during policy learning. Deployed on ANYmal (RealSense D435, Jetson AGX Xavier); latent outputs a velocity command handed to a velocity-tracking locomotion controller.

## Key results
- **Sample efficiency:** representation + policy fully trained in simulation in ~12 min (10 min state module + ~2 min policy); 2–3× faster per RL iteration than end-to-end baselines because the policy sees only the low-dim latent, and it needs no curriculum.
- **Static cluttered (1000 unseen worlds):** memory-based world-model / seq-to-seq policies converge to ~3% failure vs ~13% for the reactive (memoryless) policy, with less control effort and shorter paths. Table I: Ours 3% failure vs end-to-end CNN 10%, end-to-end CNN+LSTM 6%, blind MLP 75%.
- **Dynamic scenes:** Ours 11% failure vs reactive 25%, end-to-end CNN 20%, CNN+LSTM 15%, blind 76%. Reactive policy still avoids some obstacles but uses ~2× backward velocity (over-cautious, no velocity estimate).
- **Sim-to-real:** seq-to-seq policy transfers to ANYmal indoors/outdoors with no extra tuning; reacts to a person actively blocking its path. Notably a policy paired with an LSTM that saw *no* real data still worked on hardware — evidence the VAE latent dynamics don't diverge between sim and reality. End-to-end baselines fail on the real robot (never saw real data).
- **Ablation:** filtering the VAE target drops static collision rate from 30% → 8%; mixing real depth images (~20k real + 50k sim for the VAE; ~3 h real trajectories) is essential — without real data the policy behaves erratically on hardware.

## Limitations / open questions
- **Shortsightedness:** objects that leave the camera FoV are forgotten / not reconstructed correctly when they re-enter (training-data bias toward dominant successive frames), so collisions often happen when an obstacle exits view or enters from the side — the main residual failure mode.
- Policy uses only the current belief state, not a *dreamed* future rollout; authors suggest feeding a multi-step dreamed scene as future work.
- 2D navigation only (flat velocity commands on a cuboid); rough-terrain extension left to future work.
- Reward hand-shaping (terminal + lateral/backward velocity + distance penalties) and manual velocity-scaling tuning for the real robot.

## Concepts
- [[belief-state]] — *added 2026-07-29.* Ref `[17]` of [[auxiliary-prediction-heads]]: the RSL lineage leading to [[@yang2025spatially|SRU]]; a state representation trained to estimate the hidden state of the world, **separately** from the policy — the decoupled end of the spectrum an aux head sits in the middle of.
- [[mapless-navigation]]
- [[sim-to-real-transfer]]
- [[rl-for-legged-locomotion]]
- [[hierarchical-control]]

## My notes
This is the **VAE+LSTM predecessor** in the ETH/Hutter (RSL) learned-navigation line — the earlier point that the SRU work ([[@yang2025spatially]]) later supersedes. Worth holding onto as historical grounding for the *recurrent-policy-with-learned-latent-representation* lineage that my capability-aware G1 mid-level nav policy sits in. The core architectural bet — decouple an unsupervised latent state estimator from a small RL policy, and let the latent (not the policy) carry the sim-to-real burden — is exactly the lineage's founding move, and this paper is where the sample-efficiency and transfer arguments for it are made most cleanly (12-min training, latent dynamics that don't shift between sim and real).

Two threads to carry forward:
1. **Belief state vs. dreamed future.** The explicit limitation here — policy conditions on the current belief only, not a dreamed rollout — is precisely the gap that later recurrent/world-model nav policies try to close. Useful framing when I argue what a capability-aware policy needs to *anticipate* (e.g. terrain the robot can't yet see, or its own capability envelope) rather than just react to.
2. **Hierarchy.** The nav policy emits velocity commands to a separate velocity-tracking locomotion controller — a clean two-layer split that mirrors the mid-level-nav-over-low-level-locomotion decomposition I'm building on the G1. The forgetting-outside-FoV failure mode is a concrete reminder that a learned latent belief is not a persistent map; if capability-aware navigation needs memory of previously-seen hazards, that has to be designed in.

## Source
arXiv:2103.04351 (v1, 2021-03-07); published IEEE Robotics and Automation Letters 2021. PDF: `attachments/@hoeller2021learning.pdf`.
