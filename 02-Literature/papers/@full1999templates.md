---
type: paper
citekey: full1999templates
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Full, Robert J
- Koditschek, Daniel E
year: 1999
venue: Journal of experimental biology
doi: 10.1242/jeb.202.23.3325
arxiv: null
url: https://journals.biologists.com/jeb/article/202/23/3325/8334
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- full1999templates
- full_templates_1999
---

# Templates and anchors: neuromechanical hypotheses of legged locomotion on land

> [!info] Full, Robert J; Koditschek, Daniel E · 1999 · Journal of experimental biology

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces the "templates and anchors" framework: simple low-dimensional models (templates) capture the target locomotor behavior, while detailed morphologically grounded models (anchors) explain how many-DOF bodies realize it.
**Problem** — Legged locomotion emerges from complex body-environment interaction with far more legs, joints, and muscles than the behavior seems to need; a principled way is needed to relate simple behavioral models to the full neuromechanical system.
**Method** — A "template" is the simplest model (fewest variables/parameters) exhibiting a targeted behavior, resolving redundancy by seeking synergies and symmetries; an "anchor" is a more elaborate, biologically detailed model in which the template is embedded. The paper surveys evidence across diverse species to argue behavior is organized around such reduced models.
**Key results** — Diverse species differing in skeletal type, leg number, and posture run stably like sagittal- and horizontal-plane spring-mass systems; anchored templates suggest passive, feedforward, mechanically tuned self-stabilization can reject rapid perturbations and simplify control — with neural control dominating slow variable-frequency gaits and mechanics dominating rapid rhythmic ones.

## Takeaways
- The template (e.g., SLIP) as a reduced-order behavioral model with the anchor as its full-body embedding is the conceptual root of reduced-order planning + full-order tracking in legged robotics.
- Mechanical self-stabilization ("preflexes") can offload feedback control at high speeds — an argument for exploiting passive dynamics rather than controlling everything.
- The division of control labor (neural at low speed, mechanical at high speed) motivates hierarchical/multi-timescale controller design.

## Relevance to your work
The canonical justification for reduced-order (template) models and layered planning-and-control in legged locomotion — templates are what the planning layer plans over, anchors what the robot is. See [[@hierarchies2025motion]].

## Concepts
[[reduced-order-model]], [[hierarchical-control]]

## Source
- Cited by [[@compton2024constructive]], [[@hierarchies2025motion]]
- bibkeys: `full1999templates`, `full_templates_1999`
