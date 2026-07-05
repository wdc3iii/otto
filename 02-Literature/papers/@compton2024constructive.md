---
type: paper
citekey: compton2024constructive
tags: [control, locomotion]
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Compton, William D.
- Rodriguez, Ivan D. J.
- Csomay-Shanklin, Noel
- Yue, Yisong
- Ames, Aaron D.
year: 2024
venue: CDC 2024
doi: null
arxiv: null
url: null
zotero: null
status: read
mine: true
summary: ai-draft
pdf: attachments/@compton2024constructive.pdf
---

# Constructive Nonlinear Control of Underactuated Systems via Zero Dynamics Policies

> [!info] Compton, William D.; Rodriguez, Ivan D. J.; Csomay-Shanklin, Noel; Yue, Yisong; Ames, Aaron D. · 2024 · CDC 2024 — **my paper**

## Abstract
Stabilizing underactuated systems is an inherently challenging control task due to fundamental limitations on how the control input affects the unactuated dynamics. Decompos- ing the system into actuated (output) and unactuated (zero) coordinates provides useful insight as to how input enters the system dynamics. In this work, we leverage the structure of this decomposition to formalize the idea of Zero Dynamics Policies (ZDPs)—a mapping from the unactuated coordinates to desired Fig. 1: The two conditions required of the zeroing manifold: a) controlled actuated coordinates. Specifically, we show that a ZDP exists in invariance, and b) stable zero dynamics. a neighborhood of the origin, and prove that combining output stabilization with a ZDP results in stability of the full system variables, enabling stable zero dynamics by construction. We state. We detail a constructive method of obtaining ZDPs in prove that stabilizing to the zero dynamics surface defined by a neighborhood of the origin, and propose a learning-based the learned outputs results in stability of the overall system. approach which leverages optimal control to obtain ZDPs with This paper presents a perspective with origins in the much larger regions of attraction. We demonstrate that such a stabilization of non-minimum phase systems [5], [6], [7], paradigm can be used to stabilize the canonical underactuated sys

## Summary
> [!note] AI-drafted from the abstract/intro — a base to refine or replace with your own framing.

**TL;DR** — Formalizes **Zero Dynamics Policies (ZDPs)**: a map from a system's unactuated (zero) coordinates to *desired* actuated coordinates, which stabilizes underactuated systems without assuming the passive dynamics are already stable.
**Problem** — In underactuated systems you can't directly shape every DOF; stabilizing them when the zero dynamics aren't a priori stable is hard, and classic output design is guess-and-check.
**Method** — Decompose into actuated/unactuated coordinates and define a ZDP; prove a ZDP exists in a neighborhood of the origin and that **output-stabilization + ZDP ⇒ full-state stability**. Gives a constructive local method plus a **learning-based** ZDP (via optimal control) that enlarges the region of attraction.
**Key results** — Stabilizes the canonical cartpole and improves over nominal LQR.

## Takeaways
- Turns underactuation *structure* into leverage: control design collapses onto the low-dimensional zero coordinates.
- Learning extends the region of attraction well beyond the constructive local guarantee.
- Theory foundation for the hardware follow-up.

## Where it sits in my work
The theory behind [[@csomayshanklin2024robust|Robust Agility via Learned ZDPs]] (ARCHER hardware). Part of your zero-dynamics / underactuated-stabilization line.

## Concepts
- [[reduced-order-model]] (a ZDP is a control-oriented reduction) · _to add:_ zero-dynamics-policy, control-lyapunov-function, hybrid-zero-dynamics

## References (in otto)
- [[@ames2014rapidly]]
- [[@astrom2008feedback]]
- [[@author2021suppressed]]
- [[@bedrossian1991nonlinear]]
- [[@code2024x]]
- [[@csomayshanklin2023nonlinear]]
- [[@devasia1996nonlinear]]
- [[@duda2000pattern]]
- [[@full1999templates]]
- [[@grandia2023perceptive]]
- [[@isidori1990output]]
- [[@isidori1995elementary]]
- [[@kalman1960new]]
- [[@kearns1989computational]]
- [[@kuindersma2016optimization]]
- [[@langley2000crafting]]
- [[@liberzon2012calculus]]
- [[@machine1983learning]]
- [[@miki2022learning]]
- [[@mitchell1980need]]
- [[@newell1981mechanisms]]
- [[@raibert1984hopping]]
- [[@rodriguez2022neural]]
- [[@samuel1959some]]
- [[@sastry1999linearization]]
- [[@siekmann2021blind]]
- [[@sontag1989universal]]
- [[@sontag1999lyapunov]]
- [[@spivak2018calculus]]
- [[@tomlin1995output]]
- [[@westervelt2003hybrid]]
