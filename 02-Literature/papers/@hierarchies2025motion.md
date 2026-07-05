---
type: paper
citekey: hierarchies2025motion
tags: [control, planning, locomotion]
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors: []
year: 2025
venue: T-RO (submitted)
doi: null
arxiv: null
url: null
zotero: null
status: read
mine: true
summary: ai-draft
pdf: attachments/@hierarchies2025motion.pdf
---

# Hierarchies in Motion: From Layered Control Architectures to Perceptive 3D Hopping

> [!info] anonymized · 2025 · T-RO (submitted) — **my paper**

> [!warning] Anonymized PDF — set the real authors (updates the citekey & merges cross-citations).

## Abstract
Designing fast and flexible controllers for dynamic systems remains a fundamental challenge in robotics, particularly when balancing robustness, real-time tractability, and adaptabil- ity to complex environments. A common strategy is to decompose the control problem hierarchically, separating planning and feedback across different timescales and layers of abstraction. In this work, we leverage this hierarchical perspective and argue that it enables three key benefits: efficiency, feasibility, and generalizability. We develop constructive controller synthesis techniques for each layer of a three-layer architecture and show that their coordination enables independent design while main- taining system-layer guarantees. This framework is validated experimentally on a 3D hopping robot navigating unstructured outdoor terrain, where we show that hierarchical control enables stable, agile, and adaptive locomotion.

## Summary
> [!note] AI-drafted from the abstract/intro — a base to refine or replace with your own framing.

**TL;DR** — A journal-scale synthesis arguing that a **three-layer hierarchical control architecture** buys three things — efficiency, feasibility, generalizability — with constructive per-layer synthesis whose coordination preserves system-level guarantees.
**Problem** — Dynamic systems need controllers balancing robustness, real-time tractability, and adaptability; monolithic designs don't scale across perception/dynamics/contact complexity.
**Method** — Decompose planning and feedback across timescales/abstraction layers; develop constructive synthesis for each of three layers and show their composition gives independent design + system-layer guarantees.
**Key results** — Validated on a **3D hopping robot navigating unstructured outdoor terrain** — stable, agile, adaptive locomotion.

## Takeaways
- Positions your body of work as one coherent layered stack.
- Independent per-layer design *with* preserved end-to-end guarantees is the central claim.

## Where it sits in my work
The umbrella paper: the layers instantiate [[@csomayshanklin2025dynamically|Bézier path planning]], [[@compton2025dynamic|DTMPC]], [[@compton2025learning|predictive CBFs]], and the ZDP tracking of [[@csomayshanklin2024robust]]; formalized abstractly in [[@contract2025theory]].

## Concepts
- [[hierarchical-control]] · [[reduced-order-model]] · [[tracking-error-bound]] · [[tube-mpc]]

## References (in otto)
- [[@ambrose2022creating]]
- [[@ames1997inequalities]]
- [[@ames2017hybrid]]
- [[@amos2017optnet]]
- [[@apollondguidance]]
- [[@balas2003flight]]
- [[@bansal2017hamilton]]
- [[@barto2021reinforcement]]
- [[@bellman1957dynamic]]
- [[@borrelli2017predictive]]
- [[@bradbury2018jax]]
- [[@burridge1999sequential]]
- [[@chen2020optimal]]
- [[@chen2022interactive]]
- [[@chisci2001systems]]
- [[@codendx]]
- [[@cohen2024safety]]
- [[@compton2024constructive]]
- [[@csomayshanklin2023nonlinear]]
- [[@csomayshanklin2024dynamically]]
- [[@csomayshanklin2024robust]]
- [[@csomayshanklin2025bezier]]
- [[@da2019combining]]
- [[@deits2015efficient]]
- [[@deray2020manif]]
- [[@dixit2025step]]
- [[@donald1993kinodynamic]]
- [[@fernbach2017kinodynamic]]
- [[@fridovichkeil2018planning]]
- [[@full1999templates]]
- [[@galliker2022planar]]
- [[@gao2018online]]
- [[@geyer2006compliant]]
- [[@girard2006hierarchical]]
- [[@grandia2023perceptive]]
- [[@grey2017probabilistic]]
- [[@he2024agile]]
- [[@he2025asap]]
- [[@hereid20163d]]
- [[@incer2024layered]]
- [[@ioan2021mixed]]
- [[@jiang2001input]]
- [[@jr2024contract]]
- [[@kajita2010biped]]
- [[@kamermans2020primer]]
- [[@khalil2002nonlinear]]
- [[@kuindersma2016optimization]]
- [[@kuindersma2023recent]]
- [[@lavalle1998rapidly]]
- [[@lavalle2001randomized]]
- [[@lee2021efficient]]
- [[@liberzon2012calculus]]
- [[@lloyd1982least]]
- [[@marcucci2023motion]]
- [[@marcucci2024fast]]
- [[@marcucci2024shortest]]
- [[@matni2024theory]]
- [[@mayne2005robust]]
- [[@miki2022learning]]
- [[@pedregosa2011scikit]]
- [[@primbs2000receding]]
- [[@radosavovic2024real]]
- [[@raibert1984experiments]]
- [[@ravi2024sam]]
- [[@reher2020passive]]
- [[@rosolia2022unified]]
- [[@sarma2022internal]]
- [[@sastry1999linearization]]
- [[@scokaert1998min]]
- [[@sharf2021assume]]
- [[@stellato2020osqp]]
- [[@stoneman2014embedding]]
- [[@tabuada2009verification]]
- [[@tassa2014limited]]
- [[@tedrake2010lqr]]
- [[@tsien1952automatic]]
- [[@webb2013kinodynamic]]
- [[@wensing2023optimization]]
- [[@westervelt2003hybrid]]
- [[@xiong2024efficient]]
- [[@zardini2023co]]
- [[@zhong2020generating]]
