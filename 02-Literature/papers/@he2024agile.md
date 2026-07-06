---
type: paper
citekey: he2024agile
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-06'
authors:
- He, Tairan
- Zhang, Chong
- Xiao, Wenli
- He, Guanqi
- Liu, Changliu
- Shi, Guanya
year: 2024
venue: arXiv preprint arXiv:2401.17583
doi: null
arxiv: '2401.17583'
url: https://arxiv.org/abs/2401.17583
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@he2024agile.pdf
bibkeys:
- he2024agile
- heAgileSafeLearning2024
---

# Agile but safe: Learning collision-free high-speed legged locomotion

> [!info] He, Tairan; Zhang, Chong; Xiao, Wenli; He, Guanqi; Liu, Changliu; Shi, Guanya · 2024 · arXiv preprint arXiv:2401.17583

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Agile But Safe (ABS) is a learning-based control framework for quadrupeds that combines an agile policy with a recovery policy, switched by a learned reach-avoid value network, to achieve high-speed collision-free locomotion in cluttered spaces.
**Problem** — Legged robots in cluttered environments must be both agile (fast task execution) and safe (no collisions); prior work is either conservative (<1.0 m/s) for safety or agile while ignoring potentially fatal collisions.
**Method** — Two policies collaborate: an agile policy executes fast motor skills amid obstacles, and a recovery policy prevents failures. A learned control-theoretic reach-avoid value network governs the switch between them and also serves as the objective guiding the recovery policy, closing the loop on safety. Training (agile policy, reach-avoid value network, recovery policy, and an exteroception representation network) is done entirely in simulation.
**Key results** — Modules deploy directly to hardware with onboard sensing/computation, achieving high-speed collision-free navigation in confined indoor/outdoor spaces with both static and dynamic obstacles.

## Takeaways
- The reach-avoid value network is the safety core: it both triggers policy switching and shapes the recovery objective, giving a closed-loop safety filter learned in simulation.
- A dual-policy (agile + recovery) architecture decouples performance from safety instead of trading one against the other.
- Full sim-to-real with onboard exteroception; no explicit CBF/MPC — safety is learned via reach-avoid (HJ-reachability-style) values.

## Relevance to your work
A learned reach-avoid safety-filter alternative to CBF/MPC safety layers, and a concrete agile-yet-safe locomotion stack relevant to safety-critical and hierarchical control approaches like [[@hierarchies2025motion]].

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `he2024agile`
- arXiv: https://arxiv.org/abs/2401.17583
