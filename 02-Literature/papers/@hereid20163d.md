---
type: paper
citekey: hereid20163d
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Hereid, Ayonga
- Cousineau, Eric A.
- Hubicki, Christian M.
- Ames, Aaron D.
year: 2016
venue: 2016 IEEE International Conference on Robotics and Automation (ICRA)
doi: 10.1109/ICRA.2016.7487279
arxiv: null
url: https://doi.org/10.1109/ICRA.2016.7487279
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- hereid_3d_2016
---

# 3D dynamic walking with underactuated humanoid robots: A direct collocation framework for optimizing hybrid zero dynamics

> [!info] Hereid, Ayonga; Cousineau, Eric A.; Hubicki, Christian M.; Ames, Aaron D. · 2016 · 2016 IEEE International Conference on Robotics and Automation (ICRA)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A direct-collocation optimization framework for generating dynamic, efficient 3D walking gaits on high-DOF underactuated humanoids within the hybrid zero dynamics (HZD) framework.
**Problem** — HZD is a popular framework for dynamic underactuated bipedal walking, but scaling it to the high degrees of freedom of full humanoid robots creates severe implementation and numerical difficulties for gait generation.
**Method** — The paper poses HZD gait design as a large-scale trajectory optimization solved by direct collocation, which enables fast and reliable generation of efficient multi-contact walking gaits even under underactuation. The formulation handles the high-DOF humanoid case where prior HZD implementations struggled.
**Key results** — Demonstrates reliable generation of efficient 3D multi-contact dynamic walking gaits for underactuated humanoids; recognized as a Best Conference Paper finalist at ICRA 2016.

## Takeaways
- Direct collocation is the enabler that makes HZD gait optimization tractable at humanoid scale.
- Targets underactuated, multi-contact 3D walking rather than fully actuated flat-footed gaits.
- Underpins the FROST optimization toolchain from the Ames group for HZD-based gait design.

## Relevance to your work
Foundational HZD + direct-collocation gait-generation methodology for underactuated humanoids, the model-based lineage that layered planning-and-control frameworks like [[@hierarchies2025motion]] build on or contrast with.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `hereid_3d_2016`
