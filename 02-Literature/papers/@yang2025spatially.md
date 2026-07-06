---
type: paper
citekey: yang2025spatially
tags: [navigation, rl, method]
aliases: [SRU, Spatially-Enhanced Recurrent Unit]
created: 2026-07-06
modified: 2026-07-06
authors:
  - Fan Yang
  - Per Frivik
  - David Hoeller
  - Chen Wang
  - Cesar Cadena
  - Marco Hutter
year: 2025
venue: IJRR (arXiv preprint)
doi:
arxiv: '2506.05997'
url: https://arxiv.org/abs/2506.05997
pdf: attachments/@yang2025spatially.pdf
zotero:
status: read
mine: false
---

# Spatially-Enhanced Recurrent Memory for Long-Range Mapless Navigation via End-to-End Reinforcement Learning

> [!info] Fan Yang, Per Frivik, David Hoeller, Chen Wang, Cesar Cadena, Marco Hutter · 2025 · IJRR

## TL;DR
End-to-end RL navigation implicitly does "mapping" inside an RNN's hidden state, but standard recurrent units (LSTM, GRU, S4, Mamba) can memorize *temporal* sequences yet fail at *spatial* memorization — registering egocentric observations taken from continuously changing viewpoints into a coherent frame. The paper adds a lightweight, implicit spatial-transformation operation to LSTM/GRU (the **Spatially-Enhanced Recurrent Unit, SRU**), wraps it in an attention-based policy over a pretrained depth encoder, and trains long-range mapless navigation end-to-end with PPO from a single forward-facing stereo depth camera.

## Problem
Mapless navigation via RL needs the network to fuse the current observation `o_t` with history `H_{t-1}` into a state estimate `ŝ_t = f(o_t, H_{t-1})`. Because of ego-motion, successive observations come from different SE(3) poses, so `f` must implicitly perform the homogeneous-transformation-style registration that classical mapping pipelines do explicitly. The authors' diagnostic experiment (a synthetic landmark-recall task) shows LSTM/GRU/S4/Mamba all recall temporal category labels perfectly but produce large MSE when asked to transform and recall landmark *coordinates* into the final frame — i.e., they lack spatial registration, and the newer long-horizon SSMs (S4, Mamba) are actually *worse* spatially.

## Method
- **SRU unit.** Adds an extra term `s_t = W_xs x_t + b_s` that gates the candidate state via element-wise ("star") multiplication, e.g. for SRU-LSTM `g_t = tanh(s_t ⊙ (W_xg x_t + W_hg h_{t-1} + b_g))`. Inspired by the multiplicative form of homogeneous transformations. The full "SRU-Ours" variant adds a refined gating term (`r_t = i_t ⊙ (1 - (1-f_t)^2) + (1-i_t) ⊙ f_t^2`, `c_t = r_t ⊙ c_{t-1} + (1-r_t) ⊙ g_t`) to fight gating saturation. Drop-in modification to both LSTM and GRU.
- **Attention policy (Fig. 3).** Pretrained depth encoder (RegNet + FPN) → **self-attention** enriches the feature map with global context → **cross-attention** where the proprioceptive state `o_t^prop` (v_t, ω_t, projected gravity, previous action, relative goal `p_t`) is the *query* that compresses the 2D feature map into a 1D latent → concatenate with proprio + goal → **SRU** fuses with history → **MLP head** outputs velocity commands `a_t` at 5 Hz to a frozen learning-based locomotion controller (Lee et al. 2024) running at 50 Hz.
- **Depth encoder pretraining for sim-to-real.** The encoder is pretrained as a **VAE self-reconstruction** on large-scale synthetic depth (TartanAir), augmented with a **parallelizable depth-noise model** (edge / filling / rounding noise). Motivation: the pretrained latent distribution is wide enough to *cover* real-world depth features, giving zero-shot transfer.
- **Regularization for recurrent RL.** Sparse time-based reward (terminal + random-check `δ_check` to avoid delayed progress) trained with PPO in an asymmetric actor-critic, no curriculum. Two regularizers are "crucial" for unlocking SRU: **Deep Mutual Learning (DML)** — two policies trained in parallel with a KL distillation loss — and **Temporally Consistent Dropout (TC-Dropout)** — one dropout mask held fixed across all timesteps of a rollout.

## Key results
Simulated in NVIDIA IsaacLab across Maze / Pillars / Stairs / Pits (Fig. 6); success rate (SR) averaged over 4800 episodes / 120 environments.
- **SRU vs standard RNNs:** SRU modification alone gives +21.8% SR over LSTM/GRU; the refined gating (SRU-Ours) reaches **78.9% overall SR vs 63.5% LSTM / 61.0% GRU — +23.5%**. Biggest gains in Stairs (82.8% vs 33.1% LSTM), where 3D structure and occlusion demand spatial memory.
- **vs RL baselines:** +29.6% relative over EMHP (explicit mapping + historical path) and +105.0% over GTRL (stacked 4-frame history / Goal-guided Transformer). Swapping SRU memory into the GTRL baseline (GTRL*) alone lifts it 38.2% → 66.3% SR.
- **Attention ablation:** Spatial Attention (Ours) 78.9% vs GoT attention 68.4% vs no attention 50.5%.
- **Regularization ablation:** DML lifts SRU 65.7% → 78.9% (+24.3% relative) but LSTM only 61.8% → 63.5% — DML disproportionately unlocks SRU. TC-Dropout: 77.2% → 78.9%.
- **Range:** SRU sustains >80% SR to 50 m and >70% to 120 m; EMHP collapses below 60% past 40 m due to its fixed context window (RL training max start-goal distance was 30 m).
- **Sim-to-real:** pretraining on large-scale synthetic depth cuts Mahalanobis distance between real and RL-image latent distributions from 1.15 → 0.82, and +noise model → 0.69. Zero-shot deployment on a **Unitree B2W** legged-wheel robot (ZEDX stereo, Jetson AGX Orin, RIVR locomotion policy) across indoor office, campus main hall, outdoor terrace, and forest — traversing >100 m, rerouting around dead-ends and dynamically blocked passages.

## Limitations / open questions
- Recurrent memory still suffers **exponential decay**; "long-range" here means beyond the ~10 m local perception radius, *not* kilometer/hour-scale global navigation, which the authors say would still need an explicit/maintained global map.
- No dedicated mapping or loop-closure → deployed trajectories can drift.
- What the SRU hidden state actually *retains/transforms* is opaque (explainability gap); the authors call SRU "simple yet practical — not necessarily unique or optimal."
- Future work: combine SRU with foundation-model pretraining (DINO), auxiliary losses, and extend to manipulation / 3D reconstruction.

## Concepts
- [[recurrent-navigation-policy]]
- [[mapless-navigation]]
- [[sim-to-real-transfer]]
- [[rl-for-legged-locomotion]]
- [[hierarchical-control]]

## My notes
This is **the primary architectural anchor** for my mid-level navigation policy: a recurrent policy that outputs velocity commands over a *frozen* locomotion controller, trained with PPO / rsl_rl. The template is exactly what I want on the G1 — the difference being their deployment is on a Unitree B2W legged-wheel platform (ZEDX stereo + Jetson AGX Orin + RIVR policy), not a humanoid.

Two takeaways I care about most:
1. **Spatial vs temporal memory is the real distinction.** Their diagnostic (landmark coordinate recall) is a clean argument that LSTM/GRU/S4/Mamba capture temporal order but not egocentric spatial registration — and that the fancier long-horizon SSMs are *worse* spatially. The SRU fix is almost trivially cheap (one extra multiplicative gate motivated by homogeneous transforms), which makes it low-risk to try. Worth reproducing their synthetic recall task as a unit test before committing an architecture.
2. **The VAE depth-encoder pretraining is the precedent for my Livox Mid-360 VAE encoder plan.** Their whole sim-to-real story is: pretrain the exteroceptive encoder by self-reconstruction on *large-scale* synthetic depth (TartanAir) + a parallelizable depth-noise model, so the latent distribution is broad enough to *cover* real sensor data zero-shot. The Mahalanobis-distance evidence (1.15 → 0.82 → 0.69) is the concrete argument I'd cite. My analog: pretrain a VAE on synthetic Mid-360 point clouds/range images with a matched noise model, freeze it, feed the latent to the recurrent policy.

Also flag for my own training recipe: **DML and TC-Dropout are load-bearing, not garnish** — DML lifts SRU by +24% relative but LSTM barely moves, suggesting the spatial architecture is *underfit without regularization* because spatial memory converges slower than temporal (Fig. 1) and PPO's trust region lets the policy settle on easy temporal features first. If I adopt SRU I should budget for DML (two parallel policies + KL) and temporally-consistent dropout from the start.

Open question for me: they explicitly disclaim global navigation — memory decays, no loop closure. My use case (longer-horizon humanoid navigation) may hit exactly this wall, so the SRU may need pairing with a coarse global map or waypoint layer rather than being expected to scale alone.

## Source
arXiv:2506.05997v2 (cs.RO), submitted 2025-06-06, revised 2025-09-04; IJRR. PDF: `attachments/@yang2025spatially.pdf`. URL: https://arxiv.org/abs/2506.05997
