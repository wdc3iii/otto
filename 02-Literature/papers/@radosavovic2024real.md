---
type: paper
citekey: radosavovic2024real
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Radosavovic, Ilija
- Xiao, Tete
- Zhang, Bike
- Darrell, Trevor
- Malik, Jitendra
- Sreenath, Koushil
year: 2024
venue: Science Robotics
doi: 10.1126/scirobotics.adi9579
arxiv: '2303.03381'
url: https://doi.org/10.1126/scirobotics.adi9579
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@radosavovic2024real.pdf
bibkeys:
- radosavovic2024real
---

# Real-world humanoid locomotion with reinforcement learning

> [!info] Radosavovic, Ilija; Xiao, Tete; Zhang, Bike; Darrell, Trevor; Malik, Jitendra; Sreenath, Koushil · 2024 · Science Robotics

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A causal transformer trained with large-scale model-free RL in randomized simulation walks a real humanoid zero-shot over diverse outdoor terrain.
**Problem** — Classical humanoid controllers give impressive results but are hard to generalize and adapt to new, unstructured real-world environments.
**Method** — The controller is a causal transformer that ingests the history of proprioceptive observations and actions and predicts the next action; the authors hypothesize this history lets the model adapt in context without weight updates. It is trained by model-free RL over an ensemble of randomized simulated environments and deployed to hardware zero-shot.
**Key results** — The learned policy walks over various outdoor terrains, is robust to external disturbances, and adapts in context; deployed real-world without fine-tuning.

## Takeaways
- Transformer-over-history acts as an implicit online adaptation mechanism — "in-context" adaptation replaces explicit system identification or gain scheduling.
- Fully learning-based, sim-to-real zero-shot: strong evidence that model-free RL + domain randomization scales to full humanoid locomotion.
- Proprioception-only; no explicit terrain sensing or model — robustness is emergent, not certified.

## Relevance to your work
A flagship data point for end-to-end RL humanoid locomotion, contrasting with model-based/layered approaches; cited by [[@hierarchies2025motion]] as the learning-based counterpoint to structured motion hierarchies.

## Concepts
[[massively-parallel-simulation]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `radosavovic2024real`
