---
type: paper
citekey: schwarke2025rsl
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Schwarke, Clemens
- Mittal, Mayank
- Rudin, Nikita
- Hoeller, David
- Hutter, Marco
year: 2025
venue: arXiv preprint arXiv:2509.10771
doi: null
arxiv: '2509.10771'
url: https://arxiv.org/abs/2509.10771
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@schwarke2025rsl.pdf
bibkeys:
- schwarke2025rslrl
---

# RSL-RL: A Learning Library for Robotics Research

> [!info] Schwarke, Clemens; Mittal, Mayank; Rudin, Nikita; Hoeller, David; Hutter, Marco · 2025 · arXiv preprint arXiv:2509.10771

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — RSL-RL is a compact, GPU-only open-source RL library purpose-built for robotics: a small, easily modifiable codebase covering the algorithms most used in robotics plus robotics-specific auxiliary techniques, validated in both simulation benchmarks and real-world experiments.
**Problem** — General-purpose RL frameworks carry overhead and breadth that make them awkward to adapt for robotics research, where practitioners need to modify algorithms quickly and train efficiently in large-scale GPU simulation.
**Method** — Prioritizes a compact, hackable codebase focused on the algorithms most adopted in robotics, with auxiliary techniques for robotics-specific challenges, optimized for GPU-only training to achieve high throughput in large-scale simulation. Open-sourced at github.com/leggedrobotics/rsl_rl.
**Key results** — Demonstrated effectiveness in simulation benchmarks and real-world robotic experiments as a lightweight, extensible, practical framework for learning-based controllers.

## Takeaways
- Design philosophy is "small and modifiable over general-purpose" — the codebase is meant to be forked and edited, not configured.
- GPU-only training pairs it tightly with massively parallel simulators (e.g., Isaac Lab/Gym) for high-throughput legged-robot RL.
- The de-facto RL trainer behind much legged-locomotion work from the ETH RSL lineage.

## Relevance to your work
The lightweight GPU RL trainer commonly used to train legged-locomotion policies like those in [[@compton2025learning]], running on massively parallel simulators for high-throughput sim-to-real learning.

## Concepts
[[massively-parallel-simulation]]

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `schwarke2025rslrl`
- arXiv: https://arxiv.org/abs/2509.10771
