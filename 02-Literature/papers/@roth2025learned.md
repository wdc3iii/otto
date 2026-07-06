---
type: paper
citekey: roth2025learned
tags: [navigation, planning, method]
aliases: [FDM, Forward Dynamics Model]
created: 2026-07-06
modified: '2026-07-06'
authors:
  - Pascal Roth
  - Jonas Frey
  - Cesar Cadena
  - Marco Hutter
year: 2025
venue: "Robotics: Science and Systems (RSS)"
doi:
arxiv: '2504.19322'
url: https://arxiv.org/abs/2504.19322
pdf: attachments/@roth2025learned.pdf
zotero:
status: read
mine: false
bibkeys:
- rothLearnedPerceptiveForward2025
---

# Learned Perceptive Forward Dynamics Model for Safe and Platform-aware Robotic Navigation

> [!info] Roth, Frey, Cadena, Hutter (ETH Zurich / NVIDIA / MPI-IS) · 2025 · RSS
> [!info]- otto authors: [[marco-hutter]]

## TL;DR
A learned, perception-conditioned **Forward Dynamics Model (FDM)** predicts a legged robot's future SE(2) poses *and* per-step failure risk over a 5 s horizon, given a velocity-command sequence, a height scan, and proprioceptive history. Dropped into a zero-shot **MPPI** planner, it replaces hand-tuned traversability cost-maps with a learned, platform-specific dynamics-plus-risk model — so the planner only needs a trivial goal-distance + risk cost, no environment-specific cost engineering.

## Problem
Classical navigation stacks assess traversability with hand-designed heuristics or environment-specific cost functions that are tedious to tune and don't generalize. Physics-based dynamics models, calibrated by system identification, break down in contact-rich legged scenarios and can't cheaply capture the emergent behavior of a deep RL locomotion policy interacting with rough terrain. The authors want a scalable, heuristic-free way to know *where this specific platform (with its specific controller) can actually go* and *where it will fail*.

## Method
- **What it predicts.** An n-step ($n=10$, $\Delta t_p = 0.5$ s → 5 s horizon) transition model $\tilde f_\theta$ mapping an action sequence (linear/angular velocity commands $a\in\mathbb{R}^3$) + current observation to a sequence of future states $(p, r)$: SE(2) pose $p$ and binary failure risk $r$.
- **Inputs.** Height scan (exteroception) + 10 steps of proprioceptive history (twist commands, projected gravity, base lin/ang velocities, joint pos/vel, last two actions) at $\Delta t_h = 0.05$ s. History horizon lets the model infer terrain roughness / interaction properties.
- **Architecture.** GRU encodes proprioceptive+state history; CNN processes the height scan; their fused embedding initializes a forward-prediction GRU that consumes MLP-encoded action embeddings and emits per-step latents. Two heads: one predicts residual velocity corrections $\Delta a$ (final poses via constant-velocity integration), one predicts failure probability. Losses: MSE pose + BCE risk + an extra "stop loss" freezing pose after a predicted failure.
- **Training data.** Hybrid. Multiple simulated *years* of navigation in NVIDIA IsaacLab across 2D / 2D-3D / 3D obstacle scenarios (walls, pillars, mazes, stairs, ramps), including high-risk maneuvers unsafe on hardware; plus **real-world** ANYmal data (RTK-GNSS + IMU + Leica total-station ground truth via GrandTour) to capture out-of-sim dynamics (snow, soft vegetation, slipping). 15 rounds × 80k samples, single RTX 4090, ~8 h.
- **Planner.** Zero-shot MPPI (2048 trajectories, 7 Hz onboard, 40.6 ms/iter on Jetson Orin AGX). Reward = weighted goal-pose term + cumulative failure-risk term (summed over q neighboring paths for robustness). No cost-map, no per-environment retuning.

## Key results
- Position estimation improved **41%** (41.28%) over the perceptive FDM baseline of Kim et al. and 70.57% over a constant-velocity model at the final prediction step.
- **27% higher navigation success** in rough simulation vs. baselines; overall MPPI success ~**81%** in complex environments (88.33% in 2D, 73.75% in 3D per Table III).
- Failure/collision prediction accuracy **≥89%** across environments; F1 up to 0.9 (2D). Notably the FDM's 3D accuracy is *unaffected* by complex obstacles while the 2D-LiDAR baseline degrades — height scan sees stairs/ramps that a horizontal 2D scan cannot.
- **Platform-aware:** same action sequence yields different predicted trajectories for ANYmal, Barry (robust vs. "quiet" low-torque policy), and ANYmal-on-Wheels — the model captures the specific embodiment + locomotion policy.
- **Sim-to-real:** synthetic-only model already transfers; real-world fine-tuning further cuts mean position error 34.4% (forest), 30.6% (snow), 30.3% (pavement).

## Limitations / open questions
- Confined to a **primarily geometric domain**: assumes geometry-only terrain variation and that the locomotion policy tracks velocity commands. Fails on novel geometries (spiral staircases, tunnels/caves) or extreme conditions (ice, deep mud) outside training.
- FDM is fundamentally bounded by the **locomotion policy's capability** — it models *that* controller.
- Real-world data lacks collision demonstrations (hardware-damage risk), leaving a persistent sim-real gap on failures.
- MPPI still needs some tuning of action distribution (command ranges, time correlation), even if safety cost is heuristic-free.
- No social norms / dynamic multi-agent scenarios. Future: RGB input, adaptive timesteps, uncertainty via model ensembles.

## Concepts
- [[traversability-estimation]] — a learned forward-dynamics model *is* the traversability/feasibility predictor. · [[capability-awareness]] — model-predictive route to respecting the learned platform's capability.
- [[mapless-navigation]] — replaces explicit cost-map / traversability-map construction with a learned predictive model queried directly by the planner.
- [[sim-to-real-transfer]] — hybrid synthetic + real training; synthetic-only model transfers zero-shot, fine-tuning closes the residual gap.
- [[hierarchical-control]] — mid-level (MPPI planner + FDM) sitting above a low-level RL locomotion policy; the FDM explicitly models that lower layer.
- [[rl-for-legged-locomotion]] — the FDM is trained conditioned on a specific deployed RL locomotion policy, learning its emergent dynamics rather than rigid-body physics.

## My notes
Directly relevant to my capability-aware G1 navigation project as an **alternative mid-level formulation**: instead of a recurrent-RL nav policy that emits commands, Roth et al. keep a classical sampling-based planner (MPPI) and learn only a *forward dynamics + risk model*. The planner stays interpretable and reward-editable; the learning is quarantined into "what can this platform do and where will it fail."

The conceptual overlap with my **capability-awareness** thesis is strong but the mechanism differs. Their FDM *is* a learned capability model — it predicts, per action sequence, both the achievable future pose and the failure probability of the specific locomotion controller on the specific terrain. That is exactly "respect the learned controller's emergent capability boundary," but expressed as a **predictive failure-risk head** rather than as a value read off the low-level controller. Contrast with my line of thinking: I want the boundary to come from the LLC's own [[control-lyapunov-function]] Lyapunov value (the controller *tells* you its region of attraction / tracking competence), whereas Roth learns an *external* predictor of the same boundary from rolled-out experience. Worth articulating the trade: the CLF-value route is grounded in the controller's certificate and cheaper to trust; the FDM route needs no certificate and captures un-modeled effects (slip, soft vegetation) that no CLF sees — at the cost of being only as good as its training distribution (their own limitation section admits it's geometry-bound and controller-bound).

Also note the failure head vs. a [[control-barrier-function]] safety filter: both encode "don't enter unsafe states," but the FDM's risk is a *learned soft probability* used as a soft MPPI cost, not a hard forward-invariance constraint. Something to compare when I think about whether capability-awareness should be a hard constraint or a learned cost.

Code + models public: https://github.com/leggedrobotics/fdm — usable as a baseline / starting point for a G1 FDM.

**Extensions I want to try (from earlier reading notes):** this is the basis of what I'm trying to do on the humanoid. Concrete extensions: (1) use **latent** rather than explicit encodings of the environment; (2) **incorporate history**, so performance improves when I revisit the same area; (3) **handle uncertainty more directly** — conservative behavior when the perception is uncertain.

## Source
arXiv:2504.19322 (v2, 29 Apr 2025) · https://arxiv.org/abs/2504.19322 · To appear RSS 2025. PDF: `attachments/@roth2025learned.pdf`.
