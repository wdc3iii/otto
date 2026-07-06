---
type: paper
citekey: lee2024learning
tags: [navigation, locomotion, rl]
aliases: []
created: 2026-07-06
modified: '2026-07-06'
authors:
  - Joonho Lee
  - Marko Bjelonic
  - Alexander Reske
  - Lorenz Wellhausen
  - Takahiro Miki
  - Marco Hutter
year: 2024
venue: Science Robotics
doi: 10.1126/scirobotics.adi9641
arxiv: '2405.01792'
url: https://arxiv.org/abs/2405.01792
pdf: attachments/@lee2024learning.pdf
zotero:
status: read
mine: false
bibkeys:
- leeLearningRobustAutonomous2024
---

# Learning Robust Autonomous Navigation and Locomotion for Wheeled-Legged Robots

> [!info] Lee, Bjelonic, Reske, Wellhausen, Miki, Hutter · 2024 · Science Robotics (Vol 9, Issue 89)
> [!info]- otto authors: [[marco-hutter]]

## TL;DR
A fully integrated autonomy stack for a wheeled-legged quadruped (Swiss-Mile / ANYmal-on-wheels) built as **two RL policies stacked in a hierarchical RL framework**: a locomotion controller (LLC, 50 Hz) that fluidly blends walking and driving over rough terrain, and a mobility-aware navigation controller (HLC, 10 Hz) that issues velocity targets for local planning + path following. Validated with km-scale autonomous delivery missions in Zurich and Seville.

## Problem
Wheeled-legged robots promise fast, energy-efficient urban mobility (drive on flat ground, step over obstacles), but realizing this needs three things solved together: (1) **hybrid locomotion** — deciding when to walk vs. drive without handcrafted gait heuristics/CPGs; (2) **mobility-aware local navigation** — sampling-based planners take seconds to replan, too slow for multi-m/s robots in dynamic urban settings, and cost-map traversability ignores the robot's whole-body state; (3) **system integration** — traditionally brittle, heuristic inter-module glue. The paper collapses local planning + path following into a single learned HLC and tightly couples it to the LLC.

## Method
**Two-level HRL with an explicit velocity sub-goal** (chosen over end-to-end single-policy and over learned latent sub-goals — the authors justify the explicit interface as giving modularity and LLC reuse, enabling separate team development).

- **LLC (locomotion, 50 Hz, γ=0.99):** model-free RL + privileged learning (teacher-student, à la Miki et al.). Teacher = MLP on privileged sim state (terrain, contacts, friction, velocity); student = GRU RNN trained by DAgger imitation on noisy IMU/encoder/height-scan inputs — no state estimator, raw IMU+encoders used directly. 16-D action (12 joint positions + 4 wheel velocities). CPG/motion primitives from the prior work were **removed**; gait selection emerges. Beta-distribution bounded action space.
- **HLC (navigation, 10 Hz, γ=0.991):** PPO over a frozen LLC. Observations = **(a)** the LLC's RNN hidden/belief state (encodes terrain properties + disturbances, reused instead of proprioception), **(b)** local height map with a safety margin (3 m forward FoV; human-detection buffer zones added), **(c)** 20 previously-visited positions at 50 cm intervals (~10 m of position history via a permutation-invariant 1-D CNN/PointNet-style encoder), **(d)** two upcoming waypoints. Outputs bounded base velocities: v_x ∈ [−1.0, 2.0], v_y ∈ [±0.75] m/s, ω_z ∈ [±1.25] rad/s. Beta-distribution actions.
- **Training environment:** procedural **Wave-Function-Collapse (WFC)** terrain (stair/floor tiles) with a derived **navigation graph**; Dijkstra shortest paths give waypoints; dense geodesic-distance reward + sparse goal reward + an exploration bonus penalizing revisited buffer positions. Terrain difficulty auto-curated by a minimal-criterion filtering algorithm. Dynamic box obstacles move at 0.1–0.5 m/s.
- **Full system:** offline handheld-laser-scan → mesh → human-designed navigation graph; onboard LiDAR localization against the prior point cloud (more robust than GPS near high-rises); global Dijkstra path → "anchor-pursuit" waypoint selection → HLC → LLC.

## Key results
- **Speed & efficiency (Glattpark 8.3 km mock delivery, Zurich):** average **1.68 m/s** at **mechanical COT ≈ 0.16**, vs. a normal legged ANYmal-C at **0.55 m/s / COT 0.34** — roughly **3× faster at ~53% lower COT**. Driving actuators contribute ~0.01 COT. LLC peak **5.0 m/s** on flat (hardware max 6.3 m/s, wheel-speed limited).
- **Asymmetric traversability:** LLC can descend higher steps than it ascends (~0.6 m down vs. ~0.4 m up at high command speed; knee-collision limited going up). Traverses slopes up to ~31°, switching to a stepping gait only above ~0.5 m/s on steep slopes. Survived a 60 cm step-down with a full flight phase.
- **Navigation ablations (SPL / success over 1000 sim terrains, Table S1):** Ours **0.897 (0.901)** for 5–10 m paths, **0.689 (0.763)** for 10–20 m. Removing memory ≈ −16% SPL on long goals; no-WFC training collapses to 0.302; **end-to-end single-policy baseline fails outright (0.045 / 0.046)** — hierarchy is essential.
- **vs. conventional sampling planner (Wellhausen et al., point-goal):** Ours failure rate 30% vs. baseline 50% (memoryless variant 80%); **collision rate 0% vs. 100%** for the baseline (it overconfidently drove through occlusions with high tracking error); HLC inference **0.34 ms** vs. baseline **>1 s** replanning. Ours mean tracking error 0.24 m/s vs. 0.45 m/s.
- Deployed autonomously km-scale in **Zurich and Seville**; handled pedestrians, poles, stairs, narrow doorways, detours, with only three intervention classes (safety stop near children, untraversable tall grass, localization failure in degenerate corridors).

## Limitations / open questions
- Geometry-only perception; **no semantics** (can't distinguish pavement/lawn, relies on the human-designed graph to encode social preferences). Authors flag visual traversability / semantic segmentation as future work.
- HLC height-map FoV limited to ~3 m forward → couldn't demonstrate max 6.3 m/s hardware speed autonomously; elevation-mapping delay bottlenecks fast missions.
- Map creation still needs a ~90 min handheld scan + manual graph + hand-placed goals — human labor in the loop.
- Localization degrades in geometrically degenerate environments (long corridors).
- Optional alternating co-training of both policies gave only marginal gains, so was skipped.

## Concepts
- [[hierarchical-control]]
- [[recurrent-navigation-policy]]
- [[mapless-navigation]]
- [[rl-for-legged-locomotion]]
- [[sim-to-real-transfer]]

## My notes
This is the **most completely-specified training setup in the Hutter lineage** and the published precedent for the HLC/LLC discount-factor split I want to use.

- **Direct template for my two-tier HLC-over-frozen-LLC design.** They train the LLC first (teacher→student), freeze it, then train the HLC via PPO on top. The HLC consumes the LLC's **RNN hidden state** rather than re-observing proprioception — the belief state already encodes terrain + disturbances. This is the clean modular interface: explicit velocity sub-goals, not learned latents, precisely so the LLC is reusable and teams can develop independently. That's the argument I want to make for my stack.
- **The discount-factor precedent I was looking for — confirmed in the supplement.** Table S2 (LLC teacher): **γ = 0.99, dt = 0.02 s (50 Hz)**, max episode 10 s. Table S3 (HLC): **γ = 0.991, dt = 0.1 s (10 Hz)**, max episode 15 s. So the higher-level policy's γ *exceeds* the lower-level's despite running 5× slower — the longer effective horizon (γ/dt) belongs to the navigation layer, which makes sense: HLC needs to reason over the whole path, LLC over local dynamics. This is exactly the split I intend to publish precedent for.
- **Position-history memory is doing real work**, not decoration: 20 poses @ 50 cm (~10 m), permutation-invariant encoder. The memoryless ablation jumps from 30%→80% failure and falls into local minima / repetitive loops. Worth stealing for any partially-observed nav policy.
- WFC + navigation-graph training is a genuinely different curriculum idea (borrowed from game level generation) — structured, solvable, shortest-path-rewarded worlds beat randomly-placed obstacles/goals by a wide margin. Relevant if I ever need to generate nav curricula.
- Note the Beta-distribution bounded action space (Chou et al.) for hard velocity limits + interpretability — recurring choice in this group.

## Source
- arXiv: [2405.01792](https://arxiv.org/abs/2405.01792) (v1, 3 May 2024)
- DOI: [10.1126/scirobotics.adi9641](https://doi.org/10.1126/scirobotics.adi9641) — Science Robotics Vol 9, Issue 89 (2024)
- PDF: `attachments/@lee2024learning.pdf`
- Data/code: DOI 10.5061/dryad.gxd2547tg
