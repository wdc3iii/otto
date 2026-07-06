---
type: paper
citekey: su2025lipm
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-06'
authors:
- Su, Haokai
- Luo, Haoxiang
- Yang, Shunpeng
- Jiang, Kaiwen
- Zhang, Wei
- Chen, Hua
year: 2025
venue: 2025 IEEE-RAS 24th International Conference on Humanoid Robots (Humanoids)
doi: null
arxiv: '2509.09106'
url: https://arxiv.org/abs/2509.09106
zotero: null
summary: ai-draft
pdf: attachments/@su2025lipm.pdf
status: to-read
mine: false
bibkeys:
- su2025lipm
- suLIPMGuidedReinforcementLearning2025
---

# LIPM-Guided Reinforcement Learning for Stable and Perceptive Locomotion in Bipedal Robots

> [!info] Su, Haokai; Luo, Haoxiang; Yang, Shunpeng; Jiang, Kaiwen; Zhang, Wei; Chen, Hua · 2025 · 2025 IEEE-RAS 24th International Conference on Humanoid Robots (Humanoids)

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Uses the Linear Inverted Pendulum Model (LIPM) to shape RL rewards for stable, perceptive bipedal locomotion in the wild.
**Problem** — Learned perceptive locomotion policies struggle to stay dynamically balanced and to keep a stable camera viewpoint over rough terrain, where velocity tracking and stability can conflict.
**Method** — Derives a LIPM-inspired reward that regulates CoM height and torso orientation for dynamic balance and a steady perceptual viewpoint; a Reward Fusion Module adaptively trades velocity tracking against stability, and a double-critic architecture evaluates stability and locomotion objectives separately.
**Key results** — Simulation and real-world outdoor experiments on a bipedal robot show superior terrain adaptability, disturbance rejection, and consistent performance across a range of speeds and perceptual conditions (no numeric figures read).

## Takeaways
- The LIPM here is a *reward-shaping prior*, not a planner — a reduced-order model injected into RL rather than a model-based controller.
- Regulating torso orientation explicitly for a stable camera viewpoint couples locomotion stability with perception quality — a useful framing for perceptive legged control.
- Double-critic + adaptive reward fusion is the mechanism for resolving the classic velocity-vs-stability reward conflict.

## Relevance to your work
Directly relevant to perceptive humanoid locomotion (cited by [[@terrain2026consistent]]): it shows how a reduced-order template like the LIPM can guide learned policies toward provable-ish balance behavior and a stable sensing viewpoint.

## Reading notes (imported from prior literature vault)
> [!quote] Your own notes from reading the paper — authoritative, not AI-drafted.
- Teacher-student paradigm to train a terrain-aware locomotion policy with references shaped by the LIP model.
- LIP references: CoM tracking error, height error, roll/pitch velocity penalty. **No foot references.**
- Teacher policy trained with groundtruth information (fairly dense heightmap + privileged info: linear velocity, joint torque, feet contact force, external forces). Student policy has a heightmap predictor and a privileged predictor, trained by supervised learning to predict the heightmap and privileged info, which are then fed into the student policy during training. The heightmap predictor takes depth images via CNN + a history of proprioception via MLP, fed into a GRU.
- **My take:** the heightmap strategy is interesting — curious whether the heightmap predictor could be trained not as an encoder/decoder but just as an encoder-to-latent for RL; or pretrained as encoder/decoder, then continued in RL.

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `su2025lipm`
