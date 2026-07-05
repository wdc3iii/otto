---
type: paper
citekey: westenbroek2022lyapunov
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Westenbroek, Tyler
- Castaneda, Fernando
- Agrawal, Ayush
- Sastry, Shankar
- Sreenath, Koushil
year: 2022
venue: arXiv
doi: 10.48550/arXiv.2208.06721
arxiv: '2208.06721'
url: https://arxiv.org/abs/2208.06721
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@westenbroek2022lyapunov.pdf
bibkeys:
- westenbroek_lyapunov_2022
---

# Lyapunov Design for Robust and Efficient Robotic Reinforcement Learning

> [!info] Westenbroek, Tyler; Castaneda, Fernando; Agrawal, Ayush; Sastry, Shankar; Sreenath, Koushil · 2022 · arXiv

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Adding a control-Lyapunov-function term to the RL cost robustifies and dramatically accelerates learning of stabilizing controllers, cutting the data needed by orders of magnitude and enabling minutes-scale hardware fine-tuning.
**Problem** — RL trains complex policies in simulation, but poor sample complexity makes solving RL problems from real-world data impractical, especially for learning stabilizing controllers.
**Method** — A cost-shaping method adds a term built from a control Lyapunov function (an energy-like function from model-based control) to standard cost formulations. Theory shows the shaped costs yield stabilizing controllers even with smaller discount factors (known to reduce sample complexity), and the CLF term robustifies the search so that even highly sub-optimal policies still stabilize the system.
**Key results** — On hardware, learns stabilizing controllers for a cartpole in seconds and an A1 quadruped with a few minutes of fine-tuning; simulation benchmarks need orders of magnitude less data than standard cost designs to reach stabilizing policies.

## Takeaways
- CLF cost shaping lets you use smaller discount factors (short horizons) while still converging to stabilizing policies — the mechanism behind the sample-efficiency gain.
- The CLF term makes even sub-optimal policies stabilizing, so learning is robust, not just fast.
- Demonstrated on real cartpole and A1 hardware with seconds-to-minutes of data — a strong empirical case for injecting control theory into RL rewards.

## Abstract (from bib)
Recent advances in the reinforcement learning (RL) literature have enabled roboticists to automatically train complex policies in simulated environments. However, due to the poor sample complexity of these methods, solving RL problems using real-world data remains a challenging problem. This paper introduces a novel cost-shaping method which aims to reduce the number of samples needed to learn a stabilizing controller. The method adds a term involving a Control Lyapunov Function (CLF) – an ‘energy-like’ function from the model-based control literature – to typical cost formulations. Theoretical results demonstrate the new costs lead to stabilizing controllers when smaller discount factors are used, which is well-known to reduce sample complexity. Moreover, the addition of the CLF term ‘rob

## Concepts


## Relevance to your work
A key precursor for CLF-shaped RL rewards: the sample-efficiency and robustness argument for injecting Lyapunov certificates into learning that your CLF-RL running work builds on ([[@olkin2026chasing]]).

## Source
- Cited by [[@olkin2026stability]]
- bibkeys: `westenbroek_lyapunov_2022`
- DOI: https://doi.org/10.48550/arXiv.2208.06721
