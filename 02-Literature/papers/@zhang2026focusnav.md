---
type: paper
citekey: zhang2026focusnav
tags: [navigation, locomotion, method]
aliases: [FocusNav]
created: 2026-07-06
modified: 2026-07-06
authors:
  - Yang Zhang
  - Jianming Ma
  - Liyun Yan
  - Zhanxiang Cao
  - Yazhou Zhang
  - Haoyang Li
  - Yue Gao
year: 2026
venue: arXiv preprint
doi:
arxiv: '2601.12790'
url: https://arxiv.org/abs/2601.12790
pdf: attachments/@zhang2026focusnav.pdf
zotero:
status: read
mine: false
---

# FocusNav: Spatial Selective Attention with Waypoint Guidance for Humanoid Local Navigation

## TL;DR
A humanoid **local** navigation policy for the Unitree G1 that mimics a biological "Perception–Prediction–Attention" (PPA) loop: it predicts collision-free waypoints, anchors a cross-attention perception module to those waypoints, and dynamically *gates off* distal terrain information whenever the robot's stability drops so the policy prioritizes immediate footholds. Reaches 87% navigation success in the hardest sim scenario (dynamic obstacles + unstructured terrain) vs. 50–64% for baselines, and traverses 16 cm stairs / 22° slopes with moving pedestrians on real hardware.

## Problem
Humanoid mobile navigation in cluttered, dynamic, uneven environments has to reconcile two competing objectives at once: (1) long-range, goal-directed obstacle avoidance and (2) instantaneous locomotion stability on rough terrain. The authors argue existing approaches fail at this because (a) VLN / end-to-end methods emit velocity commands to a fixed low-level locomotion controller, which decouples high-level planning from motor control and can't support agile gait adjustments; and (b) naive feature fusion feeds the policy an undifferentiated flood of elevation/depth features, so distal-obstacle avoidance objectives conflict with local foothold-stability objectives during training.

## Method
Teacher–student pipeline, all trained in IsaacGym and deployed on the G1.

- **GuideOracle (privileged teacher).** A PPO policy with full simulator observability (precise local elevation + a traversability map + exact target coords) trained for local waypoint tracking. Reward = target-position tracking + orientation tracking; forward-motion bias restricts lateral maneuvers for gait robustness. Actions are target joint positions → PD → torques. Provides expert supervision for the vision-based student.
- **Multi-modal perception encoder.** Fuses LiDAR (Livox MID-360, long range) and depth (RealSense D435i, near-field, covers the foot blind spot) into a cross-modal point cloud, then a VoxelNet-style encoder (voxelize → 3D conv → Z-axis max-pool) produces a Bird's-Eye-View (BEV) feature. A traversability decoder is supervised with BCE loss.
- **Collision-free waypoint predictor.** A goal-conditioned **backward** autoregressive transformer: it decodes the waypoint chain in reverse chronological order starting from the goal back to the robot, so every waypoint is conditioned on the global target — this suppresses the compounding error of forward prediction. Trained with waypoint-reconstruction MSE + a latent-consistency regularizer.
- **Dual-layer spatial selective attention** (the core contribution):
  1. **WGSCA (Waypoint-Guided Spatial Cross-Attention):** predicted-waypoint latent tokens are the *queries*, BEV patches are keys/values, with a spatially-aligned position embedding so attention scores track physical proximity. This anchors feature aggregation *along the planned trajectory*, filtering background noise.
  2. **SASG (Stability-Aware Selective Gating):** a stability metric $S_m\in[0,1]$ computed from base angular velocity + Euler angles drives a Gumbel-Softmax binary gate $g$. When stable ($g{=}1$) the policy keeps distal waypoint features; when stability drops ($g{=}0$) it *truncates* far-field embeddings and refocuses on terrain under the feet: $m^h = m_1 + g\sum_{k\ge 2} m_k$.
- **Control policy.** The gated hybrid-map embedding + proprioceptive state feed a **GRU** (hidden state preserves global consistency while the gate is closed) → MLP → action. Trained by **behavior cloning** on GuideOracle, total loss = BC + traversability + waypoint + gating terms.

## Key results
Simulation (Table I; mean over 3 seeds, 100 episodes each). Hardest cell — **unstructured terrain + dynamic obstacles**, success rate:

| Method | Success % |
|---|---|
| Gallant | 50.32 |
| PGCA (proprioception-guided attention) | 63.67 |
| WGSCA-Only (ablation, no SASG) | 74.15 |
| **FocusNav** | **87.02** |

- Flat + dynamic obstacles: FocusNav 93.45% vs Gallant 68.23 / PGCA 75.45 / WGSCA-Only 84.34.
- FocusNav also leads on traverse rate, collision frequency, and the stability metric across all four terrain×obstacle cells. Notable honesty: in dynamic unstructured terrain FocusNav has *slightly higher* collision frequency than WGSCA-Only (4.56 vs 4.32) — the SASG gate trades some aggressive avoidance for self-stability to prevent falls.
- **Ablations confirm the two mechanisms are complementary:** WGSCA alone buys most of the long-range gain; SASG adds the stability/fall-prevention margin, especially on stairs (Fig. 9 shows gating activation rises sharply when transitioning from flat ground to staircases).
- **Real hardware (G1, 6 scenarios × 15 trials):** 16 cm stairs, 22° slopes, static box obstacles, dynamic pedestrians. FocusNav wins every scenario in Fig. 11 (roughly 15/15 on flat, down to ~11–12/15 on slope-dynamic and stair-dynamic), well above all baselines. Fast-LIO used for onboard localization.

## Limitations / open questions
- **Forward-only focus.** Perception concentrates on the heading direction; no coverage behind the robot → cannot handle backward maneuvers or rear obstacles.
- **Requires pre-defined goals**, no high-level semantic reasoning for long-horizon tasks (authors flag VLM integration + socially-aware navigation as future work).
- **Stability gate is a heuristic**, not a certificate: $S_m$ is a hand-tuned function of Euler angles + angular velocity, and the gate modulates *perception*, not the commands — nothing bounds the resulting locomotion behavior.
- Student is behavior-cloned, so performance is upper-bounded by the privileged GuideOracle; the low-level controller is still a fixed velocity-command tracker (the very decoupling the intro criticizes is only partially addressed).

## Concepts
- [[social-navigation]]
- [[mapless-navigation]]
- [[rl-for-legged-locomotion]]
- [[sim-to-real-transfer]]
- [[hierarchical-control]]

## My notes
This is the paper to reckon with — the direct contemporary competitor on the **exact platform** (Unitree G1, Livox MID-360 + RealSense D435i, Fast-LIO), posted Jan 2026. It kills any bare "first humanoid navigation on the G1" framing; I need to cite it and reframe around what it does *not* do.

**Where it doesn't reach (my wedge).** FocusNav is strictly *local* navigation sitting on top of a **velocity-command low-level controller**. It never touches multi-skill agile-gait *selection* (walk / run / stairs) or a learned **capability boundary** — it emits velocities to a fixed LLC and hopes the gait holds. That is exactly where my reframed contribution should live: not "navigation on the G1," but skill/gait arbitration with an explicit certified operating envelope. The authors even concede the velocity-command paradigm's rigidity in their own intro (they cite it as motivation for the attention gate) — but their fix is *perceptual*, not *control-theoretic*, so the gap stays open.

**Sharpest distinction — SASG vs. my V_t-comfort idea.** These look superficially similar and I must not let a reviewer conflate them:
- **SASG gates *perception* on a *heuristic*.** $S_m$ is an ad hoc function of Euler angles and base angular velocity; when it's low the network drops distal BEV features. It's a learned attention mask with no stability guarantee — a fall-avoidance prior baked into the input, not the objective.
- **My proposal penalizes *commands* on the LLC's own *certified* [[control-lyapunov-function]] value $V_t$.** The signal is the Lyapunov function of the locomotion policy that already carries a stability certificate; penalizing high-$V_t$ commands means the *command* respects the LLC's provable region of attraction. That's a control-theoretic comfort/feasibility notion ([[control-barrier-function]]-adjacent), not a perception heuristic. Same intuition ("back off when the body is stressed"), fundamentally different object and different guarantees. This contrast is a clean way to position my work as principled where FocusNav is empirical.

**Worth borrowing / stress-testing.** The backward (goal→robot) waypoint decoding to fight compounding error is a nice trick and orthogonal to my contribution. Their honest admission that SASG *raises* collision frequency (stability traded for avoidance) is a lever: a certified $V_t$ approach should be able to argue it gets stability *without* that trade because the guarantee, not a gate, does the work. Also note: no code released as of this note, and it's an arXiv preprint (not yet peer-reviewed).

## Source
- arXiv:2601.12790v1 (2026-01-19), cs.RO. https://arxiv.org/abs/2601.12790
- PDF: `attachments/@zhang2026focusnav.pdf` (12 pp, 11 figs).
- SJTU / Shanghai Innovation Institute.
