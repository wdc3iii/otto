---
type: paper
citekey: makoviychuk2021isaac
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Makoviychuk, V
- Wawrzyniak, L
- Guo, Y
- Lu, M
- Storey, K
- Macklin, M
- Hoeller, D
- Rudin, N
- Allshire, A
- Handa, A
- State, G
year: 2021
venue: Neural Information Processing Systems
doi: 10.48550/arXiv.2108.10470
arxiv: '2108.10470'
url: https://arxiv.org/abs/2108.10470
summary: ai-draft
pdf: attachments/@makoviychuk2021isaac.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- isaacgym
---

# Isaac gym: High performance GPU based physics simu-lation for robot learning

> [!info] Makoviychuk, V; Wawrzyniak, L; Guo, Y; Lu, M; Storey, K; Macklin, M · 2021 · Neural Information Processing Systems

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A GPU-resident physics simulator that keeps both simulation and policy training on the GPU, yielding 2-3 orders of magnitude faster RL training on a single GPU.

**Problem** — Conventional RL for robotics runs physics on the CPU and networks on the GPU, and the CPU-GPU data transfer is a severe bottleneck that limits sample throughput and forces large CPU clusters.

**Method** — Isaac Gym runs the physics simulation directly on the GPU and passes state data from physics buffers into PyTorch tensors without ever going through the CPU. This end-to-end on-GPU pipeline lets thousands of environments step and feed the policy network in parallel.

**Key results** — Reports 2-3 orders of magnitude speedups over conventional CPU-simulator RL pipelines, training complex robotics tasks on a single GPU; results and videos hosted publicly, with the simulator distributed via NVIDIA.

## Takeaways
- The core win is architectural: eliminating the CPU-GPU transfer bottleneck by keeping state in GPU buffers enables massive environment parallelism on one GPU.
- Democratizes large-scale RL for robotics — workloads that once needed CPU clusters fit on a single workstation GPU.
- It is an engineering/platform contribution (benchmark tasks provided), not a new learning algorithm; performance still depends on the underlying PhysX contact model's fidelity.

## Relevance to your work
Isaac Gym is the enabling substrate for GPU-parallel RL locomotion: it is why you can train humanoid/legged policies with thousands of parallel environments, and it underpins the learned-policy side of work like [[@compton2025learning]].

## Concepts
[[massively-parallel-simulation]]

## Source
- Cited by [[@compton2025dynamic]], [[@compton2025learning]]
- bibkeys: `isaacgym`
