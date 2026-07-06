---
type: paper
citekey: yang2022vision
tags: [locomotion, rl]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Yang, Ruihan
- Zhang, Minghao
- Hansen, Nicklas
- Xu, Huazhe
- Wang, Xiaolong
year: 2022
venue: arXiv
doi: 10.48550/arXiv.2107.03996
arxiv: '2107.03996'
url: http://arxiv.org/abs/2107.03996
zotero: null
summary: ai-draft
pdf: attachments/@yang2022vision.pdf
status: to-read
mine: false
bibkeys:
- yangLearningVisionGuidedQuadrupedal2022
---

# Learning Vision-Guided Quadrupedal Locomotion End-to-End with Cross-Modal Transformers

> [!info] Ruihan Yang; Minghao Zhang; Nicklas Hansen; Huazhe Xu; Xiaolong Wang · 2022 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — LocoTransformer fuses proprioception and depth vision in a transformer-based RL policy so a quadruped can proactively anticipate and maneuver around obstacles and uneven terrain, end-to-end.
**Problem** — Blind RL locomotion policies rely on domain randomization and proprioceptive contact measurements that only afford immediate reaction; they cannot look ahead to plan around obstacles and uneven terrain.
**Method** — An end-to-end RL method (LocoTransformer) with a transformer-based cross-modal model that combines proprioceptive state and high-dimensional depth-sensor input, letting the agent anticipate environmental changes many steps ahead.
**Key results** — Reported to significantly outperform baselines and to generalize far better, especially when transferred sim-to-real to a real robot indoors and in the wild with unseen obstacles and terrain (no numeric figures read).

## Takeaways
- Cross-modal transformer fusion of proprioception + depth vision, trained end-to-end with RL, rather than a separate perception/planning stack.
- The core argument: vision enables *proactive* maneuvering (anticipation), while proprioception is only *reactive* — motivates exteroceptive perception for terrain-aware locomotion.
- Sim-to-real transfer demonstrated on hardware with unseen obstacles/terrain.

## Relevance to your work
Directly on the perceptive/terrain-aware locomotion line — an early, influential demonstration that depth + proprioception fused via a transformer can drive end-to-end RL locomotion that transfers to hardware. Useful reference point for how much a learned visual policy anticipates versus reacts, relevant to capability-aware navigation on the G1.

## Abstract (from bib)
We propose to address quadrupedal locomotion tasks using Reinforcement Learning (RL) with a Transformer-based model that learns to combine proprioceptive information and high-dimensional depth sensor inputs. While learning-based locomotion has made great advances using RL, most methods still rely on domain randomization for training blind agents that generalize to challenging terrains. Our key insight is that proprioceptive states only offer contact measurements for immediate reaction, whereas an agent equipped with visual sensory observations can learn to proactively maneuver environments with obstacles and uneven terrain by anticipating changes in the environment many steps ahead. In this paper, we introduce LocoTransformer, an end-to-end RL method that leverages both proprioceptive states and visual observations for locomotion control. We evaluate our method in challenging simulated environments with different obstacles and uneven terrain. We transfer our learned policy from simulation to a real robot by running it indoors and in the wild with unseen obstacles and terrain. Our method not only significantly improves over baselines, but also achieves far better generalization performance, especially when transferred to the real robot. Our project page with videos is at https://rchalyang.github.io/LocoTransformer/ .

## Concepts
- [[rl-for-legged-locomotion]]
- [[sim-to-real-transfer]]
- [[traversability-estimation]]

## Source
- bibkeys: `yangLearningVisionGuidedQuadrupedal2022`
- arXiv: http://arxiv.org/abs/2107.03996
- DOI: https://doi.org/10.48550/arXiv.2107.03996
- URL: http://arxiv.org/abs/2107.03996
