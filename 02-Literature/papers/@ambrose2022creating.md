---
type: paper
citekey: ambrose2022creating
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Ambrose, Eric Ryan
year: 2022
venue: null
doi: 10.7907/gbts-va63
arxiv: null
url: https://resolver.caltech.edu/CaltechTHESIS:06012022-061623441
zotero: null
summary: ai-draft
pdf: attachments/@ambrose2022creating.pdf
status: to-read
mine: false
bibkeys:
- Ambrose
- ambrose_creating_2022
---

# Creating ARCHER: A 3D Hopping Robot with Flywheels for Attitude Control

> [!info] Ambrose, Eric Ryan · 2022 · —

## Summary
> [!note] AI-drafted from the thesis abstract — a base to refine.
**TL;DR** — A PhD thesis designing and building ARCHER, a 3D hopping robot that uses three flywheels (instead of a heavy torso) for attitude control, decoupling leg and attitude dynamics for simpler planning and control.
**Problem** — Hopping is highly underactuated with extreme, very brief ground interactions, demanding high-performance, precise actuation and fast real-time motion planning.
**Method** — Compares two vertical-hopping actuation styles (compress-release vs. moving-mass) for stability and robustness; improves the moving-mass hopper's efficiency with parallel elasticity and custom nonlinear-stiffness springs via a design-in-the-loop optimization. ARCHER then uses strategically placed flywheels to decouple the leg and attitude subsystems so each can be controlled by a separate controller.
**Key results** — Hardware experiments show the parallel-elastic second-generation moving-mass hopper is far more efficient and hops stably without closed-loop control; ARCHER demonstrated 3D hopping with independent per-subsystem controllers.

## Takeaways
- Flywheel-based attitude control decouples attitude from leg dynamics, replacing the traditional high-inertia torso and simplifying planning/control.
- Mechanical design (parallel elasticity, custom nonlinear springs) can absorb control effort — co-designing morphology and motion buys efficiency and passive stability.

## Relevance to your work
ARCHER is a shared hopping testbed in this lineage; cited in [[@csomayshanklin2024robust]] (and cohen2025safety, csomayshanklin2025dynamically, hierarchies2025motion) as the underactuated hardware platform on which robust tracking, dynamic, and safety-critical controllers are demonstrated.

## Concepts
## Source
- Cited by [[@cohen2025safety]], [[@csomayshanklin2024robust]], [[@csomayshanklin2025dynamically]], [[@hierarchies2025motion]]
- bibkeys: `Ambrose`, `ambrose_creating_2022`
- DOI: https://doi.org/10.7907/gbts-va63
