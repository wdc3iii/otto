---
type: paper
citekey: tsounis2020deepgait
tags: [locomotion, rl, planning]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Tsounis, Vassilios
- Alge, Mitja
- Lee, Joonho
- Farshidian, Farbod
- Hutter, Marco
year: 2020
venue: arXiv
doi: 10.48550/arXiv.1909.08399
arxiv: '1909.08399'
url: http://arxiv.org/abs/1909.08399
zotero: null
summary: ai-draft
pdf: attachments/@tsounis2020deepgait.pdf
status: to-read
mine: false
bibkeys:
- tsounisDeepGaitPlanningControl2020
---

# DeepGait: Planning and Control of Quadrupedal Gaits Using Deep Reinforcement Learning

> [!info] Vassilios Tsounis; Mitja Alge; Joonho Lee; Farbod Farshidian; Marco Hutter · 2020 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Combines model-based motion planning with RL by using dynamic-feasibility evaluation in place of physical simulation, training separate gait-planning and gait-execution policies for terrain-aware quadrupedal locomotion.
**Problem** — Legged robots must generalize to non-flat terrains with geometries that are hard to model or predict, requiring robustness to unforeseen situations.
**Method** — Formulate MDPs where dynamic-feasibility criteria are evaluated instead of running physical simulation. Use policy-gradient methods to independently train two policies: one that plans foothold and base motions, and one that executes them in 3D environments, using both proprioceptive and exteroceptive measurements.
**Key results** — Trained and evaluated in a challenging suite of simulated terrains — narrow bridges, gaps, stepping-stones — with policies succeeding in locomoting effectively across all cases (no numeric figures read).

## Takeaways
- Uses dynamic-feasibility criteria as a surrogate for physical simulation to define the MDP — cheaper than full sim in the loop.
- Decomposes into a foothold/base-motion planner policy and an execution policy, both trained by policy gradient.
- Consumes exteroceptive (terrain) plus proprioceptive input for gap/stepping-stone/bridge traversal.

## Relevance to your work
Relevant to terrain-aware/perceptive locomotion and to blending planning with RL — the two-level planner+executor structure is a hierarchical-control reference point for capability-aware navigation, though demonstrated in sim on quadrupeds rather than a humanoid.

## Abstract (from bib)
This paper addresses the problem of legged locomotion in non-flat terrain. As legged robots such as quadrupeds are to be deployed in terrains with geometries which are difficult to model and predict, the need arises to equip them with the capability to generalize well to unforeseen situations. In this work, we propose a novel technique for training neural-network policies for terrain-aware locomotion, which combines state-of-the-art methods for model-based motion planning and reinforcement learning. Our approach is centered on formulating Markov decision processes using the evaluation of dynamic feasibility criteria in place of physical simulation. We thus employ policy-gradient methods to independently train policies which respectively plan and execute foothold and base motions in 3D environments using both proprioceptive and exteroceptive measurements. We apply our method within a challenging suite of simulated terrain scenarios which contain features such as narrow bridges, gaps and stepping-stones, and train policies which succeed in locomoting effectively in all cases.

## Concepts
- [[rl-for-legged-locomotion]]
- [[hierarchical-control]]
- [[traversability-estimation]]

## Source
- bibkeys: `tsounisDeepGaitPlanningControl2020`
- arXiv: http://arxiv.org/abs/1909.08399
- DOI: https://doi.org/10.48550/arXiv.1909.08399
- URL: http://arxiv.org/abs/1909.08399
