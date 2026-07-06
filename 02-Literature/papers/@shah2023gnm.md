---
type: paper
citekey: shah2023gnm
tags: [navigation, method]
aliases: [GNM]
created: 2026-07-06
modified: 2026-07-06
authors:
  - Dhruv Shah
  - Ajay Sridhar
  - Arjun Bhorkar
  - Noriaki Hirose
  - Sergey Levine
year: 2023
venue: ICRA 2023
doi:
arxiv: '2210.03370'
url: https://arxiv.org/abs/2210.03370
pdf: attachments/@shah2023gnm.pdf
zotero:
status: read
mine: false
---

# GNM: A General Navigation Model to Drive Any Robot

> [!info] Shah, Sridhar, Bhorkar, Hirose, Levine (UC Berkeley / Toyota Motor North America) · 2023 · ICRA 2023

## TL;DR
A single goal-conditioned visual navigation policy — an "omnipolicy" — trained on pooled trajectory data from many structurally different ground robots generalizes zero-shot to new robots (including an underactuated quadrotor) and new environments, and beats any policy trained on a single-robot dataset. The core claim is empirical: modest design choices (temporal context + a standardized action space) let heterogeneous cross-robot data be shared productively.

## Problem
Learning-based navigation is bottlenecked by data, and robotics data is "fragmented" — every lab/robot has its own small dataset and its own policy. Can data from many distinct-but-similar robots (different cameras, viewpoints, dynamics, embodiments) be combined into one general navigation model that transfers across environments AND embodiments, so a pretrained backbone can bootstrap new robots without per-robot data collection?

## Method
Image-goal navigation: learn a goal-reaching policy π(o_t, o_G) from egocentric monocular RGB only (no GPS, no ground-truth localization). Two key ingredients make cross-robot pooling work:
- **Shared / standardized action space.** Instead of raw robot-specific commands (velocities vs. Ackermann throttle+steering, speeds spanning 0.2–10 m/s), the policy outputs *normalized* relative waypoints (x, y) and yaw change, scaled by a robot-specific top-speed factor α. Also predicts normalized temporal distance to goal (traversability estimate). A robot-specific low-level controller un-normalizes waypoints and tracks them (PID/MPPI).
- **Learned embodiment context.** Rather than hand-defining capability parameters (size, turning radius) per robot, the policy is conditioned on a temporally consistent context C_t = the last k=5 consecutive observations, from which it implicitly infers the robot's configuration/dynamics.
- **Architecture:** two MobileNetv2 encoders (one for current obs + context, one for goal), 85×64 RGB, embeddings concatenated → 3 FC layers → two heads (normalized temporal distance + τ=5 future waypoints). Trained with supervised regression (ℓ₂) plus a distance head using positive/negative trajectory pairs. Deployed on top of a topological graph: nodes are observations, edges from temporal-distance estimates, Dijkstra picks subgoals (following ViNG).

Dataset: ~60h of navigation trajectories aggregated from 6 distinct platforms (TurtleBot2, Clearpath Jackal, Warthog, Spot, Yamaha Viking ATV, RC Car) across 8 public datasets, indoor + off-road, speeds 0.2–10 m/s (table lists 70h total).

## Key results
- Deployed the *same* trained GNM zero-shot on 4 robots, including 2 not represented in training data (Vizbot/Roomba-like, DJI Tello quadrotor) plus a LoCoBot and a Jackal. GNM-Mid omnipolicy beats the best single-robot policy on every robot (Table II): e.g., LoCoBot 0.96 vs 0.62, Tello 0.99 vs 0.79, Vizbot 0.93 vs 0.51, Jackal 0.94 vs 0.68 mean success. Paper reports "up to 5× better."
- More/diverse data helps monotonically: Small (2 datasets) → Mid (4) → Large (6) improves success, e.g. LoCoBot indoor moderate 0.59 → 0.97 → 1.0 (Table III); Jackal indoor 0.42 → 0.81 → 0.88 (Table IV). Generalizes to strongly OOD settings (LoCoBot outdoors on a sidewalk; Jackal indoors in an office).
- Design-space ablation (Table V): normalized waypoints beat velocities and raw waypoints (moderate env 0.95 vs 0.54 vs 0.26); conditioned architecture beats stacked/Siamese; temporal context beats static beats none, especially in "Hard" environments (0.7 vs 0.5 vs 0.36).
- Robustness to degradation (Fig. 5, single-domain vs GNM): steering clipping 0.30 → 0.89, perturbed camera viewpoint/height 0.17 → 0.81, physical/tire damage 0.81 → 1.0. Training on varied embodiments buys robustness to sensing/actuation degradation.

## Limitations / open questions
- No explicit modeling of differing **capabilities** — all robots assumed to be ground robots (or a drone restricted to a horizontal plane) with a forward-facing RGB camera. Diverse sensing, actuation beyond speed/steering, and traversability differences are left as future work.
- Dataset is small (60h); authors expect a much larger corpus would generalize further.
- Quadrotor is artificially restricted to 2D horizontal motion 1m off the ground to mimic ground navigation — not true 3D flight.

## Concepts
- [[topological-navigation]]
- [[mapless-navigation]]

## My notes
This is the first entry in the Berkeley/Levine topological + foundation-model visual-navigation line (GNM → ViNT → NoMaD) — the longer-horizon direction for the capability-aware G1 project: sparse topological/semantic maps over dense metric SLAM. GNM's specific contribution is the *embodiment-agnostic* omnipolicy: pool data across many robots, drive any robot. The abstraction that makes pooling work — normalized action space + learned embodiment context inferred from recent observations — is elegant, but it's also exactly where the humanoid gap opens up.

Candidate project novelty to log: GNM (and this whole wheeled/aerial topo-nav line) explicitly assumes homogeneous *capability* — every node/edge is traversable the same way, and the paper flags "differences in capabilities" as unhandled future work. Nothing here addresses **capability-annotated edges** (walkable / runnable / stairs) for a multi-gait humanoid, nor combines a topological prior with OpenStreetMap as a campus-scale prior. A humanoid capability-aware topological layer — edges tagged by which gait can traverse them, fused with an OSM prior — sits precisely in the gap GNM names but does not fill. The embodiment context here is *implicit* (inferred from images); for a humanoid with discrete gaits, an *explicit* capability annotation on edges may be the more natural formulation.

## Source
arXiv:2210.03370v2 (https://arxiv.org/abs/2210.03370), presented at ICRA 2023. Project page: https://sites.google.com/view/drive-any-robot. PDF at attachments/@shah2023gnm.pdf.
