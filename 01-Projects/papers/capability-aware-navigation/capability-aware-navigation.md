---
type: project
tags: [navigation, rl, control]
aliases: [Capability-Aware Navigation, Capability-Aware Navigation RL, CAN]
status: active
created: 2026-07-06
modified: 2026-07-06
repo: /home/wcompton/repos/legged_locomotion_rl
target: IEEE conference (Olkin/Bena/Ames; TII support)
---

# Capability-Aware Navigation for the Unitree G1

> [!abstract] One-liner
> A **general, capability-driven navigation framework** for the Unitree G1 humanoid — fast
> autonomous campus traversal that *selects* speed/gait from context (walk / run / stairs)
> rather than tracking a fixed gait, layered over a **frozen CLF-RL locomotion controller**,
> with semantic (sidewalk-vs-grass) and social (human-spacing) awareness. My layer is the
> **mid-level navigation policy**. Source: [[00-Inbox/navigation_paper_brief|project brief]]
> (compiled from conversation history), codebase at `legged_locomotion_rl`.

## The distinguishing thesis — capability-awareness
The navigation policy should respect the **learned LLC's emergent capability boundary**, not
an analytical reduced-order model's assumed one. Analytical ROMs (LIP/H-LIP) cannot represent
the true feasible-command manifold of a *learned* controller, so a nav layer planning against
the analytical model is either over-conservative or commands infeasible velocities.

**Candidate contribution:** repurpose the LLC's own CLF Lyapunov value $V_t = \eta^\top P\eta$
(from [[@li2025clf|CLF-RL]] training) as a real-time **comfort signal** — penalize the nav
policy for commands that drive the LLC into high-$V$, out-of-distribution regimes. No prior art
identified that uses the learned LLC's Lyapunov value as a *navigation-level* regularizer.
See [[control-lyapunov-function]].

## Layered architecture (my ownership = middle tier)
1. **Low-level locomotion controller (LLC)** — *frozen* CLF-RL policy tracking SE(2) velocity at 50 Hz. A fixed capability primitive; the source of $V_t$. → [[@li2025clf]], [[@olkin2025chasing]] (running), [[@terrain2026consistent]] (terrain-aware sibling). See [[rl-for-legged-locomotion]], [[hierarchical-control]].
2. **Mid-level navigation policy (mine)** — recurrent policy (SRU-class/LSTM) consuming perception + goal, emitting SE(2) velocity commands to the LLC; PPO in IsaacLab via `rsl_rl`. Architecturally anchored on [[@yang2025spatially|SRU]]; HRL template from [[@lee2024learning]].
3. **Safety filter** — Poisson Safety Function / Laplace Guidance Field between the nav command and the LLC → [[@bena2025geometry]] (geometric PSF), [[@yang2026safesage|Safe-SAGE]] (semantic/social).

## Active workstreams
- **Nav policy architecture & training.** Recurrent mid-level policy over the frozen LLC, PPO/`rsl_rl`. Open: discount factor ($\gamma\approx0.997$ for dense reward + rare terminal — cf. [[@lee2024learning]] HLC $\gamma=0.991>$ LLC $0.99$), multi-goal episode design, the $V_t$-comfort reward.
- **LiDAR encoder pretraining.** VAE CNN encoder for Livox Mid-360 spherical range images (70×180, 5-channel: log-depth + normals + occlusion-edge mask), latent 256, $\beta=1.0$, free-bits 0.5, no skips, frozen during PPO. Precedent: [[@yang2025spatially]]'s TartanAir VAE encoder (robustness-first, [[sim-to-real-transfer]]).
- **Walkable-path segmentation.** Sidewalk/path vs. grass from ZED Mini. Candidate teachers: DEVA propagation, geometric depth teacher, foot-projection self-supervision (Wild Visual Navigation), VLM-prompted SAM2, multi-teacher consensus. Fusion into LiDAR via [[@vora2020pointpainting|PointPainting]]-style semantic decoration. "Walkway" definition (binary vs. continuous traversability) not yet locked.
- **Jetson deployment.** `policy_runner` on Jetson Orin AGX; ROS 2 to minipc; ONNX + CUDA EP. Open: message types, lifecycle node, artifact storage, action validation.
- **PSF derivative computation.** Exploit PDE structure of the Poisson Safety Function for $\nabla h$/Hessian vs. finite differences (known: $\mathrm{trace(Hess)}=\Delta h=\hat f$; on $\partial\Omega$, $\nabla h\parallel$ outward normal). Depends on solver representation → [[@bena2025geometry]].
- **Simulation environment.** Procedural tiles (outdoor obstacle families; indoor BSP corridors; two-mode goal sampling), real2sim pointcloud→MuJoCo (heightfield + CoACD).

## Target publication — "Capability-Aware Navigation RL"
IEEE conference (Olkin/Bena/Ames; TII support), early-stage. Standing reviewer-facing critique:
- **"Capability-aware" not yet operationalized** in the contributions.
- **Contribution 1 ("first demonstration") is contestable** given [[@zhang2026focusnav|FocusNav]] (G1, Jan 2026) — reframe around *multi-skill / agile-gait* navigation. FocusNav's SASG gates *perception* on a stability heuristic; my $V_t$-comfort penalizes *commands* on the LLC's certified CLF value — state the distinction explicitly.
- **Contribution 2 conflates** navigation-level (deployment-time CBF, [[@bena2025geometry]]/[[@yang2026safesage]]) and locomotion-level (training-time CLF reward, [[@li2025clf]]) CLF/CBF — specify the mechanism and layer.
- **Contribution 3** states the empirical result without the principled argument (analytical locomotion models cannot represent the learned controller's emergent capability boundary).

## Literature map
**In-group locomotion stack (LLC):** [[@li2025clf]] · [[@olkin2025chasing]] · [[@terrain2026consistent]]
**In-group safety stack:** [[@bena2025geometry]] · [[@yang2026safesage]]
**External navigation lineage:** [[@yang2025spatially]] (SRU, anchor) · [[@lee2024learning]] (HRL template) · [[@zhang2026focusnav]] (G1 competitor) · [[@hoeller2021learning]] (VAE+LSTM predecessor) · [[@roth2025learned]] (FDM+MPPI alt) · [[@haro2026path]] (path-conditioned) · [[@wang2026guide]] (goal-initialized mapless nav — adjacent)
**Method / architecture:** [[@wijmans2019ddppo]] (recurrent PPO) · [[@vora2020pointpainting]] (camera→LiDAR fusion)
**Topological direction (Berkeley/Levine):** [[@shah2023gnm|GNM]] · [[@shah2023vint|ViNT]] · [[@sridhar2024nomad|NoMaD]] → [[topological-navigation]]; candidate novelty = capability-annotated edges (walkable/runnable/stairs) + OSM campus prior.

## Concepts
**Thesis:** [[capability-awareness]]. **Mid-tier:** [[recurrent-navigation-policy]] · [[path-conditioned-rl]] · [[traversability-estimation]]. **Safety:** [[poisson-safety-function]] · [[social-navigation]] · [[control-barrier-function]]. **LLC:** [[control-lyapunov-function]] · [[rl-for-legged-locomotion]] · [[hierarchical-control]]. **Nav lineage:** [[mapless-navigation]] · [[topological-navigation]] · [[sim-to-real-transfer]].

## People
**Group (AMBER Lab):** [[aaron-ames]] (PI) · [[zachary-olkin]] (LLC / $V_t$) · [[ryan-bena]] (safety filter) · [[noel-csomay-shanklin]] (layered control). Target-pub byline: Olkin / Bena / Ames.
**External:** [[fan-yang]] (SRU anchor) · [[marco-hutter]] (RSL nav lineage) · [[sergey-levine]] (topological nav).

## Codebase
`legged_locomotion_rl` (talos). Two editable packages on Isaac Lab + `rsl_rl`:
`source/legged_locomotion_rl/` (LIP/CLF locomotion — teacher→distill→finetune) and
`source/nav/` (**current work**: gym nav tasks driving the LLC, VAE-pretrained frozen
lidar/depth/critic-grid CNN encoders, CUDA Poisson "safety grid" CBF layer). Nav policy =
`NavActorCritic` (single cross-attention fusion; V0→V2 version ladder = research questions).
`.claude/worktrees/ppo-rollout-profiling/` holds a PPO rollout profiling investigation
(FINDINGS + PLAN). Authoritative command list: `source/nav/README.md`.
