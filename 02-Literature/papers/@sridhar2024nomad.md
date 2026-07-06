---
type: paper
citekey: sridhar2024nomad
tags: [navigation, method, to-revisit]
aliases: [NoMaD]
created: 2026-07-06
modified: 2026-07-06
authors:
  - Ajay Sridhar
  - Dhruv Shah
  - Catherine Glossop
  - Sergey Levine
year: 2024
venue: ICRA 2024
doi:
arxiv: '2310.07896'
url: https://arxiv.org/abs/2310.07896
pdf: attachments/@sridhar2024nomad.pdf
zotero:
status: read
mine: false
---

# NoMaD: Goal Masked Diffusion Policies for Navigation and Exploration

> [!info] Sridhar, Shah, Glossop, Levine (UC Berkeley) · 2024 · ICRA 2024
> [!info]- otto authors: [[sergey-levine]]

## TL;DR
A single navigation policy that does *both* goal-directed navigation and undirected exploration, by attaching a diffusion action head to the ViNT visual-navigation Transformer and using a binary "goal mask" to toggle whether the network attends to the goal image. One network, two behaviors: mask the goal and it explores; provide the goal and it homes in.

## Problem
Navigating an *unfamiliar* environment needs two capabilities that are usually served by separate systems: task-agnostic **exploration** (search a novel space when you don't yet know where the goal is) and task-oriented **navigation** (reach a goal once it's been located/specified, e.g. via an image). Prior stacks bolt a separate high-level exploration policy or subgoal-proposal generator onto a goal-conditioned policy (e.g. ViNT + a 300M-param image-diffusion subgoal generator), which adds complexity and cost. Can one expressive policy represent both task-specific and task-agnostic behavior and switch between them?

## Method
- **Backbone.** Builds directly on ViNT: EfficientNet-B0 encoders tokenize the past 5 RGB observations plus an optional goal image; a small Transformer (4 layers, 4 heads, ~5M params) fuses them into a context vector `c_t`.
- **Goal masking.** A binary mask `m` in the attention gates the goal token. `m = 1` blocks the goal pathway → undirected exploration; `m = 0` attends to the goal → goal-conditioned navigation. During training `m ~ Bernoulli(0.5)`, so the same weights learn both modes.
- **Diffusion action head.** Rather than regressing a single action sequence (ViNT) or generating subgoal *images* (ViNT+subgoal-diffusion), NoMaD models the distribution over future action sequences directly with a diffusion policy — a 1D conditional U-Net (15 conv layers) conditioned on `c_t`, run for K=10 denoising steps to produce 8 future actions. This captures the multimodal action distribution at decision points (e.g. left vs. right at a junction) while avoiding collision-prone modes. A temporal-distance head `d(o_t, o_g)` is trained jointly.
- **Long horizon.** Follows the ViKiNG setup: pairs the low-level policy with a topological graph memory `M` and a frontier-based high-level planner for open-ended exploration and long-range goal-seeking.
- **Training.** End-to-end on GNM + SACSoN real-world datasets (100+ hours across robots/environments); MSE noise-prediction loss + weighted temporal-distance loss. Deployed on a LoCoBot, runs on onboard hardware (e.g. Jetson Orin).

## Key results
- **Exploration** (finding a goal in a novel environment): 98% success, 0.2 collisions/experiment — vs. best published baseline Subgoal Diffusion at 77% / 1.7. That's a **>25% success improvement with far fewer collisions**.
- **Efficiency:** ~19M params vs. ViNT+Subgoal-Diffusion's 335M → **~15× fewer parameters**, and it does not generate high-dimensional subgoal images.
- **Navigation** in known environments (topological graph): 90% success, matching the strong Subgoal/Random-Subgoal baselines.
- **Unified vs. dedicated (Table II):** the single goal-masked NoMaD *matches* the best dedicated models — 98% undirected (tying a standalone Diffusion Policy) and 92% goal-conditioned (tying the ViNT policy) — evidence that the two behaviors share representations rather than trading off.
- **Ablation (Table III):** the ViNT-style early-fusion encoder + attention goal-masking is critical — 98% success vs. 52% (late-fusion CNN) / 32% (ViT); ViT struggled to train end-to-end with diffusion.

## Limitations / open questions
- Goal is specified as an **image** — the authors note this is often not the most natural modality; language / spatial-coordinate goals are future work.
- Exploration uses a plain **frontier-based** high-level strategy; no semantic or prior-knowledge-driven choice of *which* region to explore.
- Purely real-world data, single wheeled platform (LoCoBot) — no gait/terrain notion; actions are 2D waypoints.

## Concepts
- [[topological-navigation]]
- [[mapless-navigation]]
- [[hierarchical-control]]

## My notes
Latest node in the Berkeley/Levine topological visual-navigation line: **GNM → ViNT → NoMaD**. GNM gave a cross-embodiment goal-conditioned policy; ViNT scaled it to a Transformer foundation model with a *separate* subgoal-diffusion module for exploration; NoMaD folds exploration back into the single network via goal masking and swaps the subgoal-image generator for a diffusion *action* head. The key conceptual move is that goal masking lets one policy be both goal-directed and undirected — exploration is just "the same policy with the goal ablated."

Relevance to the capability-aware G1 campus-traversal project:
- **Gap / candidate novelty to record.** This whole line is embodiment-agnostic at the *waypoint* level and does **not** model capability-annotated edges (walkable / runnable / stairs) for a multi-gait humanoid, nor does it use a structured campus prior (e.g. OpenStreetMap). NoMaD's topological graph edges are just "navigable per the distance predictor" — no gait semantics, no terrain typing. That is exactly the axis our project would add.
- **What to borrow.** The goal-masking / undirected-exploration mechanism is directly relevant to **dead-end escape and frontier exploration** in the campus setting: when the OSM prior fails or a route is blocked, an exploration mode that shares weights with the goal-seeking policy is attractive. The diffusion action head's ability to stay multimodal at junctions (and only collapse to a mode when a goal is provided) is a clean way to keep options open at decision points.
- Contrast with our stack's classical planning layer: NoMaD is nearly end-to-end learned (planner is just frontier + topo-graph). For a G1 we likely want the OSM/campus prior and capability edges as an explicit planning layer *above* a NoMaD-like reactive policy — i.e. push the hierarchy further than ViKiNG's frontier planner.

## Source
arXiv:2310.07896 (v1, 11 Oct 2023); ICRA 2024. https://arxiv.org/abs/2310.07896 · project page https://general-navigation-models.github.io/nomad/ · PDF at `attachments/@sridhar2024nomad.pdf`.
