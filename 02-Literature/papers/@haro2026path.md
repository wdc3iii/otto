---
type: paper
citekey: haro2026path
tags: [navigation, rl, planning]
aliases: []
created: 2026-07-06
modified: 2026-07-06
authors:
  - Mateo Haro
  - Julia Richter
  - Fan Yang
  - Cesar Cadena
  - Marco Hutter
year: 2026
venue: arXiv preprint (cs.RO)
doi:
arxiv: '2603.13888'
url: https://arxiv.org/abs/2603.13888
pdf: attachments/@haro2026path.pdf
zotero:
status: read
mine: false
---

# Path-conditioned Reinforcement Learning-based Local Planning for Long-Range Navigation

> [!info] Haro, Richter, Yang, Cadena, Hutter (ETH RSL) · 2026 · arXiv

## TL;DR
An RL local-navigation policy that *conditions* on a coarse global reference path as **contextual guidance** rather than a hard constraint to follow. Because the reward is purely goal-reaching (no path-following term), the policy learns to opportunistically exploit good path info and ignore bad path info — big efficiency gains when the path is good, no degradation when the path is noisy, wrong, or absent.

## Problem
Long-range navigation is usually hierarchical: a global planner emits a path, chopped into waypoints, followed sequentially by a local planner. Two failure modes: (1) if the local planner is trained/encouraged to follow the path closely, bad remote-sensing paths produce locally infeasible waypoints that wreck local execution; (2) if the local planner sees only a single next waypoint / minimal global context, it falls back on reactive exploration — dead-ends, backtracking, circuitous routes over long horizons. Goal: get the long-horizon efficiency of global guidance without inheriting the brittleness of trusting it.

## Method
Extends the ETH spatially-enhanced-recurrent-memory mapless nav framework [Yang et al. 2025, ref 7]. POMDP with egocentric depth camera + proprioception; policy outputs velocity commands at 5 Hz to a separate 50 Hz locomotion policy.
- **Observation** adds a full reference path `P_t` = fixed-length sequence of N=15 waypoints in the robot's egocentric frame (entire path, not a truncated look-ahead segment). Each waypoint encoded as a 4-vector: normalized direction + log-compressed distance, so it generalizes across path lengths/geometries.
- **Path Encoding Module**: self-attention over waypoints (captures global structure — turns, deviations, alternatives) + cross-attention with a *learned query* that lets the policy attend to the most informative path regions (sharp turns, critical deviations). Path embedding is concatenated with the SRU output; the path is assumed fixed within an episode so it bypasses the recurrent memory.
- **Training path generation is the key trick**: don't train only on optimal paths. Sample from a controlled distribution of feasible-but-suboptimal paths — A* on a PRM for optimal, plus Greedy Best-First Search with a detour-biased heuristic (attraction to a random detour point) for sub-optimality — then line-of-sight smoothing + per-waypoint noise perturbation (some paths become partially infeasible). This exposure teaches the policy *when to trust* the path.
- **Reward has NO path-following term**: task (goal-reaching), regularization (smoothness, momentum-filtered action), penalties (collision, body inclination), plus a "shortcut reward" that rewards making large along-path progress in one step — reinforcing behaviors that bypass unnecessary detours the path suggests. Trained with Asymmetric Actor-Critic PPO in Isaac Lab / rsl-rl; 1046 agents, 180 procedural envs, 39.5 h on one RTX 4090; domain randomization instead of curriculum.

## Key results
- **Optimal path**: SR 0.87 / SPL 0.82 vs baseline (no path) SR 0.83 / SPL 0.75 — ~**7% SPL improvement** from exploiting good paths.
- **Degraded (noisy + suboptimal) path**: SR 0.83 / SPL 0.74 — essentially baseline-level, i.e. bad path info does **not** hurt. This asymmetry (helps when good, harmless when bad) is the headline.
- Evaluated on larger terrains (50×50 m) than trained (30×30 m), longer horizon (120 s vs 60 s), up to 2250 episodes.
- **Ablations**: (a) architecture — learned-query self+cross-attention has steepest learning curve and best reward vs direct concatenation / self-attention-only / fixed-random-query; (b) training — models trained *without* path noise are much less robust on degraded paths at test (Noise Ablation collapses to SPL ~0.2), confirming noisy-path exposure is what buys robustness.
- **Missing-input robustness**: zero out the path → behaves like baseline (relies on perception); zero out depth → navigates by waypoints alone (works for shorter, less-perturbed paths). So each modality is independently usable.
- **Real-world**: deployed zero-shot on a Unitree B2W quadruped (ZED-X depth cam, Jetson AGX Orin, LiDAR-based state estimation) in an unseen university building; long runs ~93 m and ~91 m. Notably a path chosen to *avoid stairs* (not minimize distance) is followed opportunistically — the policy honors the safer intent without rigid tracking.

## Limitations / open questions
- **Fixed N=15 waypoint representation** caps the number of turns / spatial extent it can encode; authors flag this as a scalability limit for hundreds-of-meters routes and want variable-length path processing.
- Learned reliance on path quality is **implicit** — set by the training path distribution, hard to tune or predict, and at inference the policy **cannot explicitly distinguish accurate from unreliable guidance** (it treats all observed paths uniformly). Proposed fix: an explicit path-reliability observation, or gating path features on the SRU's internal state / interaction history.

## Concepts
- [[path-conditioned-rl]]
- [[recurrent-navigation-policy]]
- [[mapless-navigation]]
- [[hierarchical-control]]
- [[sim-to-real-transfer]]
- [[rl-for-legged-locomotion]]

## My notes
Directly relevant to the **capability-aware G1 navigation** project, specifically the **path-segmentation → navigation interface**. The active walkable-path-segmentation workstream (segmenting sidewalks/paths from the ZED Mini) produces exactly the kind of *coarse, imperfect reference path* this paper is designed to consume — and this is arguably the cleanest published answer to "how do I feed a segmented path into a locomotion/navigation RL policy without the policy breaking when the segmentation is wrong?"

Key takeaways for our interface design:
- **Condition, don't constrain.** Feed the segmented path as an *observation*, keep the reward purely goal-reaching. This decouples navigation success from segmentation quality — a bad sidewalk mask degrades gracefully to baseline exploration instead of driving the robot off a cliff. That is the property we want when the perception stack is imperfect.
- **The robustness comes from the training distribution, not the architecture.** The noise-ablation collapse (SPL 0.82 → 0.2) says: if we adopt this, we must train on *deliberately corrupted* segmented paths (noisy, partially infeasible, sometimes absent), ideally sampled to mimic our actual ZED-Mini segmentation failure modes, not clean A* paths.
- **Same lab lineage as our stack**: built on Yang et al. 2025 SRU mapless nav, Isaac Lab + rsl-rl, deployed on a Unitree quadruped. Transfer to a G1 pipeline is plausible; the locomotion policy is a separate 50 Hz layer, matching our RL-locomotion / classical-planning split.
- **The stair-avoidance real-world result is the capability-aware hook**: a path encoding *intent* (avoid stairs) that the policy respects opportunistically is conceptually close to encoding G1 capability limits into the reference path itself.
- **Open gap worth watching / possibly contributing**: their acknowledged inability to signal path *reliability* at inference. Our segmentation stack could emit a per-segment confidence — feeding that as the explicit path-reliability observation they propose is a concrete extension. Also the fixed-15-waypoint cap will bite on real outdoor sidewalk distances.

## Source
arXiv:2603.13888v1 [cs.RO], 14 Mar 2026 · https://arxiv.org/abs/2603.13888 · PDF at `attachments/@haro2026path.pdf`. All authors at Robotic Systems Lab (RSL), ETH Zürich. Code publicly released (per paper). Supported by SNSF project No.227617.
