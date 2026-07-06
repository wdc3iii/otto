---
type: paper
citekey: compton2024dynamic
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-06'
authors:
- Compton, William D
- Csomay-Shanklin, Noel
- Johnson, Cole
- Ames, Aaron D
year: 2024
venue: arXiv preprint arXiv:2411.15350
doi: null
arxiv: '2411.15350'
url: https://arxiv.org/abs/2411.15350
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@compton2024dynamic.pdf
bibkeys:
- compton2025dynamic
- comptonDynamicTubeMPC2024
---

# Dynamic Tube MPC: Learning Tube Dynamics with Massively Parallel Simulation for Robust Safety in Practice

> [!info] Compton, William D; Csomay-Shanklin, Noel; Johnson, Cole; Ames, Aaron D · 2024 · arXiv preprint arXiv:2411.15350
> [!info]- otto authors: [[aaron-ames]] · [[noel-csomay-shanklin]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Learns a *dynamic tube* — tracking error as a function of the planning model's actions — from massively parallel simulation, then optimizes plans so the tube stays in free space, trading performance against safety online.
**Problem** — Planning on a reduced-order model plus tracking on the full dynamics leaves inevitable tracking error; robustifying via worst-case bounds is conservative because it ignores that some planning trajectories are easier to track than others.
**Method** — Massively parallel simulation is used to learn a dynamic tube representation characterizing tracking performance as a function of the planning model's actions. Planning-model trajectories are then optimized so the resulting dynamic tube lies in free space, yielding a Dynamic Tube MPC that trades safety against performance in real time.
**Key results** — Demonstrated on the 3D hopping robot ARCHER, enabling agile navigation of cluttered environments and safe, collision-free traversal of narrow corridors.

## Takeaways
- The tube is *state/action-dependent* rather than a fixed worst-case bound — the key departure from classical tube MPC.
- Massively parallel simulation is the enabler for learning the tube dynamics at scale.
- Couples reduced-order planning and full-order tracking through a learned error model embedded in the MPC.

## Relevance to your work
This is the direct precursor to [[@compton2025dynamic]] — the dynamic-tube-as-learned-object idea and the ARCHER hopper hardware carry straight through to your dynamic tube MPC line of work.

## Concepts
[[dynamic-tube]] [[tube-mpc]] [[reduced-order-model]] [[tracking-error-bound]] [[massively-parallel-simulation]]

## Source
- Cited by [[@compton2025learning]]
- bibkeys: `compton2025dynamic`
- arXiv: https://arxiv.org/abs/2411.15350
