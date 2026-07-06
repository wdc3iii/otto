---
type: paper
citekey: shah2023vint
tags: [navigation, method]
aliases: [ViNT]
created: 2026-07-06
modified: 2026-07-06
authors:
  - Dhruv Shah
  - Ajay Sridhar
  - Nitish Dashora
  - Kyle Stachowicz
  - Kevin Black
  - Noriaki Hirose
  - Sergey Levine
year: 2023
venue: CoRL 2023
doi:
arxiv: '2306.14846'
url: https://arxiv.org/abs/2306.14846
pdf: attachments/@shah2023vint.pdf
zotero:
status: read
mine: false
---

# ViNT: A Foundation Model for Visual Navigation

> [!info] Shah, Sridhar, Dashora, Stachowicz, Black, Hirose, Levine (UC Berkeley) · 2023 · CoRL 2023 (oral)

## TL;DR
ViNT is a 31M-parameter Transformer trained as a *foundation model* for image-goal
visual navigation: a single goal-conditioned policy, pre-trained on 100+ hours of
navigation from 8 robot platforms, that generalizes zero-shot to new robots and
environments and fine-tunes to new tasks/goal modalities with under an hour of data.
Paired with a diffusion subgoal proposer and a topological-graph planner, it solves
kilometer-scale navigation.

## Problem
What does a *foundation model for mobile robotics* look like? Prior navigation policies
are specialists — trained on a single platform, a single environment, or one goal-spec
type (PointGoal, GPS, image-goal). The paper wants one high-capacity policy that (i)
deploys zero-shot across sensors/embodiments/environments and (ii) adapts to downstream
tasks (new objectives, new goal modalities) with little data.

## Method
- **Task = image-goal navigation.** Requires only videos + actions; no ground-truth
  localization, semantic labels, or metadata — so it trains on heterogeneous multi-robot
  data. Input: current + P=5 past RGB observations plus a subgoal image; output: (i)
  temporal distance to the subgoal and (ii) H=5 future waypoint actions.
- **Architecture.** Two EfficientNet-B0 encoders tokenize observations (d=512). Goal
  fusion is *relative*: the goal image is stacked channel-wise with the current
  observation and passed through a separate encoder, so the model encodes the difference
  to goal rather than the goal in isolation (naive goal encoding ignored the goal).
  Tokens + positional encoding feed a decoder-only Transformer (4 layers, 4 heads).
- **Embodiment-agnostic action space.** Relative waypoints normalized by each robot's top
  speed; a robot-specific PD controller un-normalizes and tracks them at 4Hz,
  receding-horizon. This abstracts away low-level control differences across platforms.
- **Long-horizon = graph + diffusion.** An episodic *topological graph* stores past
  observations as nodes, edges = ViNT-predicted reachability/distance. An image-to-image
  **diffusion model** proposes diverse short-horizon subgoal candidates from the current
  observation; ViNT spatially grounds them (distance + action rollout), and an A*-like
  planner scores them with a goal-directed heuristic (Euclidean, GPS, or satellite image)
  to drive exploration toward a distant goal.
- **Downstream adaptation.** Full fine-tuning to new environments/embodiments (~1h data),
  and *prompt-tuning*-style adaptation to new goal modalities (GPS waypoints, high-level
  routing commands) by learning a small soft-prompt network into the shared goal-token
  space.

## Key results
- **Undirected goal-reaching (physical search):** ViNT 0.94 indoor / 1.00 outdoor success,
  vs End-to-End BC 0.72/0.44, GCG 0.61 outdoor, RECON 0.19/0.23. The random-subgoal
  ablation (ViNT-R) reaches 0.81 indoor — diffusion subgoals matter.
- **Kilometer-scale guided exploration (vs ViKiNG/RECON prior SOTA):** Indoor-position
  0.90 success / 91m; Outdoor-GPS 0.95 / 0.84 SPL / 1270m; Outdoor-satellite 1.00 / 0.94
  SPL / 1040m — beats ViKiNG on success, SPL, and distance across the board.
- **Zero-shot cross-embodiment (max displacement w/o intervention):** ViNT drives a Go1
  quadruped (unseen in training) 45m vs GNM 8m / single-robot 12m; LoCoBot 120 vs 60/40;
  Jackal 438 vs 427/184. Exhibits *positive transfer* — outperforms specialists even on
  in-domain robots (Vizbot 110 vs 40).
- **Fine-tuning (CARLA driving, <1h data):** ViNT 0.82 image-goal success (0.82 in-lane),
  0.89 positions, 0.72 routing — beats GNM, ImageNet, SimCLR, VC-1 pre-training and
  from-scratch; ~40% success zero-shot before fine-tuning, ~80% after, beating a
  single-domain model trained with 5x the data.

## Limitations / open questions
- No system identification / sensor homogenization across robots — relies on each robot's
  own low-level controller, so deployment still needs a per-robot velocity tracker.
- Subgoal diffusion samples in image space (not latent); latent sampling led to poor
  performance — flagged as future work.
- Image-goal spec is unintuitive for many real tasks; longer-horizon / semantic goals
  require the graph + heuristic scaffolding on top.
- Ground robots + a drone/quadruped, all with roughly planar egocentric camera motion —
  no multi-gait or terrain-affordance reasoning.

## Concepts
- [[topological-navigation]]
- [[mapless-navigation]]
- [[sim-to-real-transfer]]
- [[hierarchical-control]]

## My notes
This is the foundation-model center of the Berkeley/Levine topological visual-navigation
line — GNM (multi-robot dataset + embodiment-agnostic policy) → **ViNT** (scale it into a
goal-conditioned Transformer foundation model) → NoMaD (fold the diffusion subgoal
proposer into the policy itself). For the capability-aware G1 project this is the
*longer-horizon* alternative to dense SLAM: a sparse topological/semantic graph with
image-subgoal edges, planned over with a goal-directed heuristic, rather than a metric
occupancy map. The diffusion-subgoal + A*-on-graph structure is exactly the
[[hierarchical-control]] decomposition I want — high-level graph planner over a
learned local goal-reaching policy.

**Where the gap is (candidate novelty).** ViNT's edges encode reachability/temporal
distance, and its heuristic context is geometric (GPS/Euclidean) or a satellite prior.
It does *not*:
1. annotate edges with **capabilities** (walkable / runnable / stairs / traversable-only-at-gait-X)
   — critical for a multi-gait humanoid where an edge's cost depends on which locomotion
   controller is available;
2. carry a **semantic map prior** like OpenStreetMap for a campus — its "prior" is raw
   satellite imagery scored by a learned heuristic, not a structured routing graph.

So the humanoid capability-aware topological layer — edges tagged with which gait can
execute them, grounded in an OSM campus prior — is genuinely orthogonal to what this line
addresses. ViNT is the right backbone/precedent to cite for the topological + image-subgoal
architecture; the contribution sits in the edge semantics, not the graph mechanism.

## Source
arXiv:2306.14846v2 · https://arxiv.org/abs/2306.14846 · CoRL 2023 (oral).
Project page: general-navigation-models.github.io. PDF at attachments/@shah2023vint.pdf.
