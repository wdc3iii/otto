---
type: paper
citekey: yang2026safesage
tags: [navigation, control, hardware]
aliases: [Safe-SAGE, Laplace Guidance Field, LGF]
created: 2026-07-06
modified: 2026-07-06
authors:
  - Lizhi Yang
  - Ryan M. Bena
  - Meg Wilkinson
  - Gilbert Bahati
  - Andy Navarro Brenes
  - Ryan K. Cosner
  - Aaron D. Ames
year: 2026
venue: IROS 2026 (accepted)
doi:
arxiv: '2603.05497'
url: https://arxiv.org/abs/2603.05497
pdf: attachments/@yang2026safesage.pdf
zotero:
status: read
mine: false
---

# Safe-SAGE: Social-Semantic Adaptive Guidance for Safe Engagement through Laplace-Modulated Poisson Safety Functions

> [!info] Yang, Bena, Wilkinson, Bahati, Navarro Brenes, Cosner, Ames · 2026 · IROS 2026

## TL;DR
Geometric safety filters (CBFs, HJ reachability) are *semantically blind* — a human and a chair of equal volume produce identical avoidance behavior. Safe-SAGE injects class-level semantics into the safety layer by shaping a **Laplace guidance field** with class-dependent repulsion and a tangential passing bias, then feeding it as the forcing term of a **Poisson safety function**. The result: safety margins that grow faster near humans than near walls, plus socially-compliant passing side, all while retaining forward-invariance guarantees. Runs on Go2 and G1 hardware.

## Problem
Established safe-set methods (artificial potential fields, MPC, CBFs, HJ reachability) build the safe set from geometry alone — user-defined primitives, learned occupancy, or geometric shapes. Because a human and an object of equal geometric volume yield identical safe sets, controllers are forced to be either universally conservative (poor performance in clutter) or universally aggressive (safety failures). Hand-tuned state-dependent relaxations exist but cannot autonomously incorporate context. Meanwhile LLMs/VLMs *can* reason about semantics and social norms but run at low frequency with high latency — a modality mismatch that blocks their direct use in a real-time safety filter. Safe-SAGE targets this neuro-symbolic gap: make context-dependent, socially-aware safety a first-class property of the execution-rate safety layer.

## Method
Layered safety architecture positioned between perception and control, operating on a first-order reduced-order model with full state ζ = (q, ψ), q = (x,y) planar position, ψ heading.

- **Perception & tracking.** Fuse multi-sensor point clouds into a robot-centric occupancy grid; a vision instance-segmentation net (YOLOv11n) labels human instances; an object-level tracker (connected-component clustering + greedy nearest-neighbor association, exponential-decay velocity estimates) maintains persistent semantics *beyond the camera FoV*, so a human tracked out of frame keeps its label.
- **Laplace Guidance Field (LGF), v_sem.** Solve a *vector* Laplace Dirichlet BVP over free space. Boundary conditions are class-aware: outward-normal repulsion of magnitude b(q,ψ) < 0 on obstacle boundaries (more negative b ⇒ wider margin + earlier activation), plus a *tangential* bias λ on an internal Dirichlet interface (buffered from obstacle boundaries via a Pontryagin difference) that sets the passing side (e.g. pass-on-the-left) and how strongly social flow dominates off the surface. The field is non-conservative (nonzero curl) — that is exactly what lets it encode rotational social-flow patterns. By Hopf's Lemma the outward normal of v is ∝ ∇h on the boundary, giving the generalized safety constraint vᵀk ≥ −γh.
- **Poisson Safety Function (PSF), h_full.** Construct the scalar safety function by solving Poisson's equation Δh_full = f̂(∇·v_sem) with zero Dirichlet BC, using the guidance-field divergence as the forcing term. The class-aware boundary conditions propagate through the forcing function, so h_full rises faster near semantically-critical (human) boundaries. Forward invariance is proven per-slice (Theorem 1, via Nagumo).
- **Temporal variation.** Estimate ∂h_full/∂t by motion-compensated finite differences over consecutive PSF solutions + low-pass filter, forward-propagated over the horizon for proactive avoidance of *closing* obstacles.
- **Dual-layer safety filter.** (1) An **MPC layer**: SQP-solved horizon optimization with linearized CBF constraints from the semantic LGF, σ-scaled to avoid over-conservatism far from obstacles. (2) A **real-time closed-form analytical filter** at the state-update rate that projects u_mpc onto the safe set via trilinear interpolation of the 2D heading slice — reflexive reactivity to dynamic hazards. Class distinction enters upstream through b(q,ψ), so the class-agnostic-looking filter still yields class-dependent margins.

## Key results
- **Class-dependent margins (Table I, Fig. 3).** With b_human = −1.7, b_objects = −0.5: human-robot margin **0.318 ± 0.077 m** vs baseline (nominal PSF, b_human = b_objects = −1.0) **−0.008 ± 0.063 m** — the proposed method keeps a positive human berth where the baseline effectively grazes the human. Max lateral offset (willingness to pass on the far side of the human): **0.75 m** vs **−0.1 m**.
- **Platform-agnostic hardware.** Deployed on the **Unitree Go2** quadruped (front UTLidar + top Livox Mid360 + gimbaled RealSense D435) and, because it acts on a reduced-order model, transferred with minimal changes to the **Unitree G1 humanoid** (single forward-facing D435 + two lidars).
- **Real-world scenarios.** Hallway with pedestrians walking toward/away, open area with sensory noise, and a crowded cafeteria — maintains social norms (consistent passing side) and safety in dynamic environments.
- Simulation benchmark (Fig. 4) shows the trajectory keeping a larger, tangentially-curved berth around a human (H) than around a static obstacle (O), consistent with b_human < b_objects.

## Limitations / open questions
- Safety layer is on a **first-order reduced-order model**; extension to higher-order dynamics is left to future work (tracking controller on learned full-order dynamics, ref SHIELD [46], or high-order CBFs).
- Class-dependent b and tangential λ are **hand-tuned per class**; principled or learned assignment is explicitly deferred.
- **Theorem 1 is a per-slice (fixed-ψ) guarantee.** ∂h_full/∂ψ is not perfectly parallel to the inward normal on the lifted boundary, so Nagumo doesn't directly apply in the coupled heading channel — closed only via an ISSf-style robustness term or σ-scaling of the heading derivative, not a clean full-state proof.
- No occupancy-grid *memory* or semantic graph yet; LLM reasoning integration is stated as future work.

## Concepts
- [[poisson-safety-function]] — Laplace-modulated PSF is the safety-function construct.
- [[social-navigation]] — class-aware margins + tangential passing bias for socially-compliant motion.
- [[control-barrier-function]] — the safety filter enforces CBF-QP constraints; the PSF's 0-superlevel set is a CBF-defined safe set.
- [[hierarchical-control]] — layered perception → semantic-field synthesis → dual (MPC + analytical) safety filter, above the locomotion controller.
- [[mapless-navigation]] — navigates from a robot-centric onboard occupancy grid with no prior global map.

## My notes
This is the **semantic/social layer of the Poisson Safety Function stack** — the direct sequel to the geometry-aware PSF work ([@bena2025geometry]). It fixes the exact gap that makes geometric CBFs unusable for my capability-aware G1 navigation project: the safety layer cannot tell a human from a chair of equal volume. Safe-SAGE's move is elegant — don't touch the CBF machinery, instead push class semantics *upstream* into the boundary conditions of the Laplace/Poisson BVPs (b_human = −1.7 vs b_objects = −0.5), and let them propagate into the safety function so margins are context-dependent by construction. The tangential-bias term is the "social-spacing / passing-side" requirement, and the repulsion-magnitude term is essentially the "sidewalk-vs-grass" traversability weighting I want — both instantiated *inside the safety filter* rather than bolted on as a planner heuristic.

Points worth pulling into my own work:
- The **reduced-order-model** framing is why it drops onto the G1 unchanged — same argument as the ROM-based safety line I care about (note ref [35] here is the Cohen/Csomay-Shanklin/**Compton**/Molnar/Ames reduced-order-model safety-synthesis paper — my own work is in this lineage).
- The **per-slice-only** forward-invariance caveat is the honest weak point: heading is not covered by the clean guarantee. For humanoid navigation where yaw matters a lot, that ISSf patch is the thing to scrutinize.
- Complementary to RL locomotion: this sits *above* the walking policy on a ROM, so it composes with a learned low-level controller rather than competing with it.

Follow-ups: read [@bena2025geometry] for the base PSF/LGF construction; the b/λ hand-tuning is an obvious place where a learned or capability-derived assignment could plug in.

## Source
arXiv:2603.05497v3 (submitted 2026-03-05, v3 2026-06-22). Accepted to IROS 2026 (copyright transferred to IEEE). https://arxiv.org/abs/2603.05497 · PDF at `attachments/@yang2026safesage.pdf`.
