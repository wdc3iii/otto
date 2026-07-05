---
type: paper
citekey: li2025gait
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Li, Junheng
- Duan, Ziwei
- Ma, Junchao
- Nguyen, Quan
year: 2025
venue: 'Robotics: Science and Systems XXI'
doi: null
arxiv: '2502.02934'
url: https://arxiv.org/abs/2502.02934
summary: ai-draft
pdf: attachments/@li2025gait.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- li_gait-net-augmented_2025
---

# Gait-Net-augmented Implicit Kino-dynamic MPC for Dynamic Variable-frequency Humanoid Locomotion over Discrete Terrains

> [!info] Li, Junheng; Duan, Ziwei; Ma, Junchao; Nguyen, Quan · 2025 · Robotics: Science and Systems XXI

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A Gait-Net-augmented implicit kino-dynamic MPC that jointly optimizes step location, step duration, and contact forces for natural variable-frequency humanoid walking over discrete terrain.
**Problem** — Optimization-based humanoid controllers rely on fixed-time discretization, so they cannot adapt step duration and placement simultaneously, limiting responsiveness and performance on challenging terrain.
**Method** — A Gait-Net-augmented Sequential Convex MPC solves the multi-linearly-constrained problem via iterative quadratic programs, while a lightweight Gait-frequency Network (Gait-Net) predicts the preferred step duration expressed as variable MPC sampling times, reducing step-duration optimization to the parameter level.
**Key results** — Validated in high-fidelity simulation and on small-scale humanoid hardware, demonstrating variable-frequency and 3-D discrete-terrain locomotion using only a one-step preview of terrain data.

## Takeaways
- Learns step *frequency* (via Gait-Net) rather than solving for it inside the MPC, sidestepping the fixed-timestep limitation while keeping the QP structure tractable.
- Implicit kino-dynamic formulation couples timing, footholds, and forces in one convex-approximation loop — a middle ground between reduced-order and full contact-implicit MPC.
- Only a one-step terrain preview is needed, making it practical for reactive discrete-foothold walking.

## Relevance to your work
Cited for variable-frequency MPC and learned step-timing over discrete footholds — directly adjacent to discrete-terrain humanoid locomotion as in [[@dai2025walk]].

## Concepts
[[reduced-order-model]] [[hierarchical-control]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `li_gait-net-augmented_2025`
