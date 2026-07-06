---
type: paper
citekey: siekmann2020memory
tags: [locomotion, rl]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Siekmann, Jonah
- Valluri, Srikar
- Dao, Jeremy
- Bermillo, Lorenzo
- Duan, Helei
- Fern, Alan
- Hurst, Jonathan
year: 2020
venue: arXiv
doi: 10.48550/arXiv.2006.02402
arxiv: '2006.02402'
url: http://arxiv.org/abs/2006.02402
zotero: null
summary: ai-draft
pdf: attachments/@siekmann2020memory.pdf
status: to-read
mine: false
bibkeys:
- siekmannLearningMemoryBasedControl2020
---

# Learning Memory-Based Control for Human-Scale Bipedal Locomotion

> [!info] Jonah Siekmann; Srikar Valluri; Jeremy Dao; Lorenzo Bermillo; Helei Duan; Alan Fern; Jonathan Hurst · 2020 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Recurrent (RNN) policies for sim-to-real bipedal locomotion outperform memoryless ones in simulation and, with dynamics randomization, transfer better to hardware while using memory for online system identification.
**Problem** — Controlling a non-statically-stable biped is hard due to complex hybrid dynamics; prior RL work used simple memoryless networks, even though memory-based architectures excel in other RL domains.
**Method** — Use recurrent neural networks (RNNs) for sim-to-real biped locomotion so policies can learn to use internal memory to model important physical properties; train with dynamics randomization to curb overfitting to simulation physics.
**Key results** — RNNs significantly outperform memoryless policies in simulation but fail to transfer better on the real biped unless trained with dynamics randomization, which yields consistently better sim-to-real transfer; RNNs can encode dynamics parameters into memory to perform online system identification (no numeric figures read).

## Takeaways
- Memory helps in sim but overfits to sim physics on hardware — dynamics randomization is what makes recurrent policies transfer.
- Learned memory states act as online system identification, encoding dynamics parameters.
- Human-scale biped (Cassie-class) case for RNN policies over memoryless MLPs.

## Relevance to your work
Directly relevant to RL locomotion policy architecture and sim-to-real for human-scale bipeds like the G1: the finding that memory only pays off on hardware alongside dynamics randomization, and that recurrence enables implicit system ID, informs policy design choices.

## Abstract (from bib)
Controlling a non-statically stable biped is a difficult problem largely due to the complex hybrid dynamics involved. Recent work has demonstrated the effectiveness of reinforcement learning (RL) for simulation-based training of neural network controllers that successfully transfer to real bipeds. The existing work, however, has primarily used simple memoryless network architectures, even though more sophisticated architectures, such as those including memory, often yield superior performance in other RL domains. In this work, we consider recurrent neural networks (RNNs) for sim-to-real biped locomotion, allowing for policies that learn to use internal memory to model important physical properties. We show that while RNNs are able to significantly outperform memoryless policies in simulation, they do not exhibit superior behavior on the real biped due to overfitting to the simulation physics unless trained using dynamics randomization to prevent overfitting; this leads to consistently better sim-to-real transfer. We also show that RNNs could use their learned memory states to perform online system identification by encoding parameters of the dynamics into memory.

## Concepts
- [[rl-for-legged-locomotion]]
- [[sim-to-real-transfer]]

## Source
- bibkeys: `siekmannLearningMemoryBasedControl2020`
- arXiv: http://arxiv.org/abs/2006.02402
- DOI: https://doi.org/10.48550/arXiv.2006.02402
- URL: http://arxiv.org/abs/2006.02402
