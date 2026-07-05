---
type: paper
citekey: kajita2010biped
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Kajita, Shuuji
- Morisawa, Mitsuharu
- Miura, Kanako
- Nakaoka, Shin'ichiro
- Harada, Kensuke
- Kaneko, Kenji
- Kanehiro, Fumio
- Yokoi, Kazuhito
year: 2010
venue: 2010 IEEE/RSJ International Conference on Intelligent Robots and Systems
doi: 10.1109/iros.2010.5651082
arxiv: null
url: https://doi.org/10.1109/iros.2010.5651082
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- kajita2010biped
---

# Biped walking stabilization based on linear inverted pendulum tracking

> [!info] Kajita, Shuuji; Morisawa, Mitsuharu; Miura, Kanako; Nakaoka, Shin'ichiro; Harada, Kensuke; Kaneko, Kenji · 2010 · 2010 IEEE/RSJ International Conference on Intelligent Robots and Systems

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A biped walking stabilization framework that reduces a full humanoid (HRP-4C) to a linear inverted pendulum with ZMP delay and stabilizes walking by tracking that reduced model.
**Problem** — Stabilizing dynamic biped walking on a high-DOF humanoid, robustly enough to handle turning and uneven outdoor terrain.
**Method** — A body posture controller and foot force controllers are built on top of the robot's joint-position servo; with this posture/force control layer in place, the whole robot behaves like a simple linear inverted pendulum (LIP) with ZMP delay. After a preliminary experiment confirming the linear dynamics, a tracking controller for the LIP is designed for walking stabilization.
**Key results** — Demonstrated on the 42-DOF humanoid HRP-4C walking and turning on a lab floor, and additionally walking outdoors on uneven pavement.

## Takeaways
- Canonical example of reduced-order-model control: posture/force loops render the full robot as a LIP so a simple template controller stabilizes it.
- The layered structure (joint servo → posture/force → LIP tracking) is an early hierarchical locomotion stack.
- Key modeling assumption is the ZMP-delay LIP approximation, validated empirically before controller design.

## Relevance to your work
A foundational template-based locomotion stabilizer: reducing a humanoid to a LIP and tracking it is the reduced-order/layered pattern underlying modern hierarchical locomotion planning. See [[@hierarchies2025motion]].

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `kajita2010biped`
