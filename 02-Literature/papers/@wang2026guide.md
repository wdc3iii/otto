---
type: paper
citekey: wang2026guide
tags: [navigation, rl]
aliases: [GUIDE, Goal-Initialized Directional Understanding]
created: 2026-07-06
modified: 2026-07-06
authors: [Liang Wang, Jin Jin, KanZhong Yao, YiBin Wu, Fangqiang Ding, Jin Wang, Jun Wu, Zhe Sun, Qiuguo Zhu]
year: 2026
venue: arXiv preprint
doi:
arxiv: 2606.10832
url: https://guide-navigation.github.io/
pdf: attachments/@wang2026guide.pdf
zotero:
status: read
mine: false
---

# GUIDE: Goal-Initialized Directional Understanding for End-to-End Visual Navigation

> [!info] Wang, Jin, Yao, Wu, Ding, Wang, Wu, Sun, Zhu · 2026 · arXiv (cs.RO)

## TL;DR
A fully end-to-end RL navigation policy for legged robots that receives the goal **only once, at episode start** ($t=0$), then navigates cluttered spaces and mazes with **no streaming goal/localization updates**. The trick: an auxiliary **spatial anchor predictor** trained on privileged sim state teaches the policy to maintain internal egomotion and directional awareness from proprioception + raw depth, so it holds a persistent spatial context without an external localizer or map.

## Problem
Learning-based legged navigation typically feeds the policy a **continuously updated relative goal** from a hierarchical state-estimation/localization stack. That (a) adds sensory + compute overhead and (b) breaks the claim of "map-free, end-to-end" autonomy. Under partial observability, policies trained this way also tend toward **myopic behavior** — getting trapped in dead ends and local minima. The paper asks whether a purely end-to-end policy can sustain **long-horizon directional awareness** with the target given only at initialization — the RL analogue of biological "cognitive maps" [Tolman 1948].

## Method
- **Task = goal-initialized POMDP.** Robot gets an initial egocentric relative target $g^0=[x^0_g,y^0_g,\psi^0_g]$ at $t=0$; thereafter only onboard proprioception + depth. Objective: policy $\pi_\theta(a_t \mid o_t, \mathcal{O}_t, \hat{c}_t)$ conditioned on the predicted spatial context $\hat c_t$.
- **Hierarchy.** High-level nav policy at **10 Hz** emits twist commands $[v_x, v_y, \omega_z]$; low-level locomotion controller at **50 Hz** executes them (locomotion trained à la Long et al.). See [[hierarchical-control]].
- **Multi-frequency proprioception.** Two streams — a **low-freq history** (10 Hz, N=10) for broad temporal context and a **high-freq recent** stream (200 Hz, M=20) for fine transient dynamics — fused via self-attention + GRU into a proprio token $z^p_t$.
- **Spatial anchor predictor (the core idea).** Three lightweight MLP heads predict, from proprioception, the robot's **body velocity $\hat v_t$**, **relative target position $\hat g_t$**, and **relative spawn position $\hat s_t$**, supervised during training by privileged sim states (Huber + L2 loss, Eq. 1). This auxiliary signal forces $z^p_t$ to encode egomotion + long-horizon position — the "internal directional awareness."
- **Visual branch.** 8-frame depth buffer ($30\times43$), shared CNN encoder → temporal self-attention → cross-attention (proprio token as query, vision tokens as K/V) → GRU → spatial latent $z^s_t$.
- **Training.** Asymmetric actor-critic via **PPO**. Privileged **critic** sees downsampled top-down occupancy + explored-region maps. **Multi-Critic (MuC)** splits reward into sparse-task vs dense-shaping groups with separate value heads, combining normalized GAE advantages (Eq. 3). Reward = sparse tracking ($r_{pos}, r_{head}$) + dense progress shaping (Euclidean for clutter, **maze-graph connectivity distance** for mazes). Procedural **cluttered** (alleys, L-corners, pillars) and DFS-generated **maze** terrains under a difficulty/distance curriculum.

## Key results
- **Simulation (1000 episodes × 50 layouts, 4 benchmarks).** Full GUIDE: SR ~99.9% easy clutter/maze; **99.6% hard maze** (AT 22.1 s, CR 4.8%). Nearly matches the ground-truth oracle variants (GUIDE-GT-Inference / GT-Train), showing the *learned* internal context ≈ privileged state.
- **Ablations.** Removing **high-freq proprioception** collapses everything (hard-maze SR 99.6→0.01%; target-tracking error 0.23→3.37 m) — fine-grained motion cues are essential to egomotion. **w/o Velocity Prediction** hurts most among the three heads (reactive collision avoidance); **w/o Target Prediction** worse than w/o Spawn (target gives direct goal guidance). **w/o Multi-Critic** drops hard-maze SR to ~49%.
- **Real world (zero-shot).** 8×8 m in-lab clutter + mazes, robot auto-halts when internal goal-distance <0.2 m. **Final Distance** to true goal ~0.2–0.3 m (i.e. ≤0.1 m avg estimation error), best across all metrics. Also deployed in-the-wild: office corridors, outdoor grass with dense vegetation, dynamic obstacles — stable with raw onboard sensing only. Hardware: DEEP Robotics quadruped.

## Limitations / open questions
- **Narrow depth FoV** is the main constraint: minor collisions on sharp turns in tight corridors; robot sometimes **overlooks traversable openings** when escaping a dead end and re-enters the same trap before recovering (Fig. 6). Future work: active perception / added sensor modalities.
- Anchor prediction relies on **privileged sim supervision** — needs a good sim; no discussion of long-run drift over very long episodes.
- Quadruped only; no humanoid results.

## Concepts
- [[mapless-navigation]] — goal given once, no online localization/map; the paper's whole premise.
- [[rl-for-legged-locomotion]] — model-free PPO, asymmetric actor-critic, sim-to-real.
- [[hierarchical-control]] — 10 Hz nav policy over 50 Hz locomotion controller.
- [[sim-to-real-transfer]] — zero-shot deployment of a policy trained purely in sim.

## My notes
Directly relevant to my navigation-autonomy line. The **spatial anchor predictor** is a clean idea: instead of *bolting on* a localizer, use privileged sim state as an **auxiliary supervision target** so the policy internalizes egomotion — related in spirit to Yang et al. [4] (spatially-enhanced recurrent memory, continuous updates) and Wijmans et al. [42] ("emergence of maps" in blind agents), but the goal-initialized-only setting is the sharper claim. Contrast with my CLF/CBF-certified line: this is the opposite pole — no stability/safety certificate, robustness purely learned, and safety left implicit in reward + depth reactivity (CR still 3–8%). Worth thinking about whether the anchor-prediction auxiliary loss could be *married* to a certifiable local safety filter. The multi-frequency (10/200 Hz) proprio split for egomotion is a concrete, borrowable design detail. Note the author overlap with the Oxford/Bonn robotics groups (Yao, Ding, Y. Wu — adjacent to the leg-IMU proprioceptive state-estimation line, ref. [3] Doglegs, not yet in otto).

## Source
arXiv:2606.10832 [cs.RO], submitted 2026-06-09. Project: https://guide-navigation.github.io/ · PDF: `attachments/@wang2026guide.pdf`. Full text read.
