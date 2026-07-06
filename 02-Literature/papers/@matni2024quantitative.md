---
type: paper
citekey: matni2024quantitative
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Matni, Nikolai
- Ames, Aaron D
- Doyle, John C
year: 2024
venue: IEEE Control Systems Magazine
doi: 10.1109/MCS.2024.3382388
arxiv: null
url: https://doi.org/10.1109/MCS.2024.3382388
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- matni2024quantitative
---

# A Quantitative Framework for Layered Multirate Control: Toward a Theory of Control Architecture

> [!info] Matni, Nikolai; Ames, Aaron D; Doyle, John C · 2024 · IEEE Control Systems Magazine
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A tutorial/framework article proposing a quantitative theory of layered control architectures (LCAs) — the universal design pattern of stacking controllers across spatiotemporal scales — spanning robotics, power grids, human sensorimotor control, and the Internet.
**Problem** — Complex engineered and natural control systems must operate robustly across many spatiotemporal scales on constrained hardware/software, yet the layered architectures they use are designed by heuristic and lack a unifying quantitative theory.
**Method** — The authors argue that a common design pattern — layered control architectures (LCAs) — recurs across vastly different domains, and set out to formalize it. The article develops a quantitative framework for layered, multirate control as a step toward a genuine theory of control architecture (analyzing how layers at different rates interact and what each contributes to robustness/performance).
**Key results** — A conceptual and quantitative framework rather than a single experiment; positions LCAs as the central object of study and offers tools to reason about layering and multirate structure quantitatively.

## Takeaways
- Frames "control architecture" itself as a first-class object worthy of quantitative theory, not just individual controllers.
- Layering across spatiotemporal/rate scales is presented as a universal pattern — the same lens applies to robots, grids, biology, and networks.
- Useful as the conceptual grounding for why locomotion stacks are layered (planning / MPC / low-level control at different rates) rather than monolithic.

## Relevance to your work
This is the theoretical charter for why locomotion autonomy is built as a layered, multirate stack (planner → reduced-order MPC → whole-body control); it is cited by [[@compton2025learning]] and the dynamic-planning work to justify and quantify the layered-architecture choice.

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@compton2025learning]], [[@csomayshanklin2025dynamically]]
- bibkeys: `matni2024quantitative`
