---
type: person
tags: [control, locomotion, planning]
aliases: [Noel Csomay-Shanklin]
created: 2026-07-06
modified: 2026-07-06
affiliation: Caltech — AMBER Lab (Control & Dynamical Systems)
role: Robotics researcher (PhD, CDS, Caltech 2025); Senior Robotics/AI Engineer, Figure AI
homepage: https://noelc-s.github.io/website/
scholar: https://scholar.google.com/citations?user=-sNgzuwAAAAJ
github: https://github.com/noelc-s
twitter: https://x.com/noel_c_s
---

# Noel Csomay-Shanklin

> [!info] PhD, Control & Dynamical Systems (Caltech, 2025) · AMBER Lab (Aaron Ames) → Figure AI · [homepage](https://noelc-s.github.io/website/) · [scholar](https://scholar.google.com/citations?user=-sNgzuwAAAAJ)

> [!note] AI-drafted bio — grounded in public sources (below); verify and refine. See uncertainty flags in **Sources**.

## Bio
Robotics researcher who completed his PhD in **Control & Dynamical Systems at Caltech** (2025) in
Aaron Ames's **AMBER Lab**, working on the theory and hardware of dynamic legged locomotion. His
thesis line is **hierarchical / layered control** — provably combining high-level optimization-based
planning with low-level certifiable stabilization ([[control-lyapunov-function|CLFs]] + MPC) — realized
on 3D hopping robots and bipedal walkers. He is now a **Senior Robotics/AI Engineer at Figure AI**
(a humanoid company).

## Contributions to the field
- **Layered control architectures with certificates.** A central theme: treat control as a stack of
  layers running at different rates/clocks, and *certify* the interface between them — e.g. Bézier
  reachable polytopes as dynamic-feasibility certificates for a planning layer, and multi-clock
  layered systems ([[@incer2024layered]], [[@csomayshanklin2024bezier]], [[@csomayshanklin2022multi]]).
- **Reduced-order-model + tube-based robust safety.** Synthesizing safety-critical controllers on
  [[reduced-order-model|reduced-order models]] and learning [[dynamic-tube|tube dynamics]] so
  guarantees transfer to the full-order robot ([[@cohen2025safety]], [[@compton2025dynamic]]).
- **Zero-dynamics policies + CBF/CLF learning for locomotion.** Learning low-dimensional
  [[control-barrier-function|CBF]]/zero-dynamics representations that make bipedal walking both
  agile and safe ([[@csomayshanklin2024robust]], [[@rodriguez2022neural]], [[@csomayshanklin2021episodic]]).
- **NMPC for underactuated dynamic robots.** Whole-body / Lie-group NMPC for 3D hopping and planar
  bipeds ([[@csomayshanklin2023nonlinear]], [[@galliker2022planar]]).

## Relevance to otto
This page exists because Noel is the **AMBER-lab collaborator most entangled with my own line** — my
most frequent co-author here (co-first on **Robust Agility**, [[@csomayshanklin2024robust]]). We are
building the same program: **certifiable layered control for legged robots**, where a certificate at
each layer boundary lets an aggressive planner sit on top of a stabilizing tracker without losing
guarantees.
- **Shared spine — layered control + ROMs + tubes.** [[hierarchical-control]] over a
  [[reduced-order-model]] with a [[dynamic-tube|tube]] bounding the model-vs-reality gap is the exact
  architecture my [[tube-mpc|Dynamic Tube MPC]] work sits in ([[@compton2025dynamic]],
  [[@compton2024dynamic]]) — Noel is a co-author, and [[@cohen2025safety]] (ROM safety synthesis) is
  the safety-layer companion to it.
- **Co-authored core.** [[@csomayshanklin2024robust]], [[@compton2024constructive]] (zero-dynamics
  policies), [[@compton2025dynamic]], [[@cohen2025safety]], [[@hierarchies2025motion]] — these are the
  papers where our work overlaps directly.
- **Contrast worth tracking.** Noel's instinct is **optimization + certificates first** (reachable
  polytopes, multi-clock layered proofs) as the primary path to guarantees; my recent line pushes
  **learning inside the loop** (massively-parallel sim to *learn* the tube / zero dynamics) and then
  certifies. Same target — robust dynamic locomotion with proofs — approached from the
  optimization-certificate vs. learned-model ends. His move toward humanoids at Figure AI is a bet
  that this layered-control theory transfers to full-scale humanoids, which is exactly my G1 question.

## In otto — authored works
_Papers in [[02-Literature/index|Literature]] he (co-)authored (18):_

**Layered / hierarchical control architectures**
- [[@hierarchies2025motion]] — *Hierarchies in Motion: From Layered Control Architectures to Perceptive 3D Hopping*
- [[@incer2024layered]] — *Layered Control Systems Operating on Multiple Clocks*
- [[@csomayshanklin2022multi]] — *Multi-Rate Planning and Control of Uncertain Nonlinear Systems (MPC + CLFs)*

**Reduced-order models · robust / safe planning · tubes**
- [[@compton2025dynamic]] · [[@compton2024dynamic]] — *Dynamic Tube MPC: Learning Tube Dynamics with Massively Parallel Simulation* (ICRA 2025 / arXiv)
- [[@cohen2025safety]] — *Safety-Critical Controller Synthesis with Reduced-Order Models*
- [[@csomayshanklin2025bezier]] · [[@csomayshanklin2024bezier]] — *Bézier Reachable Polytopes* (ACC 2025 / arXiv)
- [[@csomayshanklin2025dynamically]] · [[@csomayshanklin2024dynamically]] — *Dynamically Feasible Path Planning via Reachable Bézier Polytopes* (ICRA 2025 / arXiv)

**CLF / CBF · zero-dynamics · learning for locomotion**
- [[@csomayshanklin2024robust]] — *Robust Agility via Learned Zero Dynamics Policies* (co-first with me)
- [[@compton2024constructive]] — *Constructive Nonlinear Control of Underactuated Systems via Zero Dynamics Policies*
- [[@rodriguez2022neural]] — *Neural Gaits: Learning Bipedal Locomotion via CBFs and Zero Dynamics Policies*
- [[@csomayshanklin2021episodic]] — *Episodic Learning for Safe Bipedal Locomotion with CBFs*

**NMPC / hopping / bipedal hardware**
- [[@csomayshanklin2023nonlinear]] — *NMPC of a 3D Hopping Robot: Lie Group Integrators*
- [[@galliker2022planar]] — *Planar Bipedal Locomotion with Nonlinear MPC*
- [[@reher2020passive]] — *Passive Dynamic Balancing and Walking in Actuated Environments*
- [[@chen2022interactive]] — *Interactive Multi-Modal Motion Planning with Branch MPC*

_(Note: he is cited but is **not** an author of [[@yang2026safesage]], so it is excluded above.)_

## Elsewhere (non-paper)
- Personal site: <https://noelc-s.github.io/website/>
- AMBER Lab: <http://www.bipedalrobotics.com/people.html>
- Google Scholar: <https://scholar.google.com/citations?user=-sNgzuwAAAAJ>
- GitHub: <https://github.com/noelc-s> · X/Twitter: <https://x.com/noel_c_s> · YouTube: <https://www.youtube.com/@noelc-s>
- Talk: *A Hierarchical Perspective on Robotic Control* (Montreal Robotics, on YouTube)

## Sources
- Personal website (self-authored, most current): role, PhD field, "Senior Robotics/AI Engineer at Figure AI," links.
- AMBER Lab people page + LinkedIn (via search): PhD 2025; research summary (hierarchical/optimization-based control, CLF+MPC, 3D hopping, bipeds).
- Google Scholar profile for publication list.
- Current role confirmed by the vault owner: **Senior Robotics/AI Engineer at Figure AI** (an earlier NYU Assistant Professor plan was superseded).
- **Uncertainty flags (verify before citing):**
  1. Advisor **Aaron Ames** inferred from AMBER Lab affiliation (not explicitly stated on the fetched personal-site content).
  2. Bézier/Dynamic-Tube/Dynamically-Feasible pairs appear as two notes each (arXiv preprint + published version) — likely the same work at different stages.
