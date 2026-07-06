---
type: paper
citekey: bena2025geometry
tags: [navigation, control, hardware]
aliases: [Poisson Safety Function, PSF]
created: 2026-07-06
modified: 2026-07-06
authors:
  - Ryan M. Bena
  - Gilbert Bahati
  - Blake Werner
  - Ryan K. Cosner
  - Lizhi Yang
  - Aaron D. Ames
year: 2025
venue: IEEE-RAS Intl. Conf. on Humanoid Robots (Humanoids)
doi:
arxiv: '2508.11129'
url: https://arxiv.org/abs/2508.11129
pdf: attachments/@bena2025geometry.pdf
zotero:
status: read
mine: false
---

# Geometry-Aware Predictive Safety Filters on Humanoids: From Poisson Safety Functions to CBF Constrained MPC

## TL;DR
Turns raw perception occupancy into a control barrier function by solving Poisson's equation over free space (a Dirichlet BVP), then extends that construction two ways — a moving-boundary version for dynamic obstacles and a configuration-space lifting that adds orientation DOFs — and enforces it inside an MPC+CBF predictive safety filter. Demonstrated in real time on a Unitree G1 humanoid and Go2 quadruped, letting the robot *reorient* its asymmetric body to squeeze through gaps rather than treating itself as a conservative disk.

## Problem
Safety-critical navigation for legged robots in unstructured, dynamically-changing environments. Two gaps in prior safe-set machinery: (1) safety functions are usually either *ad hoc* analytic shapes (circles, ellipses) or signed distance functions — neither derived from live perception, and both blind to true robot shape; (2) the standard Poisson safety function [Bahati/Ames prior work, ref 18] is *static* (fixed domain) and treats the robot as a point/disk, so it can't handle moving obstacles or exploit the fact that an asymmetric humanoid can rotate to fit through a narrow gap. Reducing the robot to a single inflation radius injects large conservatism for elongated geometries (e.g. a humanoid carrying an oblong payload).

## Method
Three contributions layered on the Poisson safety function idea.

- **Spatial Poisson safety function (baseline, from ref 18).** Treat free space as domain Ω = int(C) with boundary ∂Ω = ∂C taken directly from an occupancy map. Solve the Dirichlet problem Δh₀ = f on Ω, h₀ = 0 on ∂Ω, with a superharmonic forcing term f < 0. The solution h₀ is smooth (C^∞) on the domain, is positive in the interior and zero on obstacle boundaries, and is provably a valid CBF for single-integrator dynamics. So the CBF is *synthesized numerically from perception* with no analytic obstacle model.
- **Temporal extension → moving boundary value problem.** Make the safe set time-varying C_T(t). Track the evolving boundary with a level-set / transport-equation view: ∂φ/∂t + v·∇φ = 0. Under a constant velocity field over the MPC horizon, the future boundary is the current boundary advected by ∫v dτ (eq. 21), giving a linear boundary-prediction model ∂C_T(t) = {y : φ₀(y − v̄t) = 0}. This builds a non-cylindrical space-time domain Ω_T ⊂ ℝ³×[0,T] on which a parameterized (moving-boundary) Dirichlet problem for h_T(y,t) is posed. Obstacle velocities estimated online via OpenCV optical flow on the camera stream.
- **Geometric lifting → configuration space via Minkowski difference.** Let R(q) ⊂ ℝ³ be the set of points the robot body occupies at attitude q ∈ 𝕊³ (quaternion). Define the reduced safe set C_Q(q) = C ⊖ R(q) (Minkowski *difference*; equivalently in practice a convolution of the occupancy map with a robot-shaped kernel). Lift the domain into a higher-D configuration space (ℝ³×𝕊³, or ℝ²×𝕊¹ in the planar demos) so the Poisson safety function h_Q(y,q) now carries rotational DOFs. Because only translational output y needs to be safe, q does not need a boundary condition and drops out of the Laplacian — keeping the PDE tractable. This is what lets the robot pivot to open an otherwise-blocked gap.
- **Predictive safety filter (MPC+CBF).** Combine both extensions into h_QT(y,q,t) over a space-time-configuration domain. Use a fully-actuated reduced-order single-integrator model (3-DOF: two translation + one rotation, χ = [x,y,θ], input μ = [v_x, v_y, ω]). Solve a finite-time optimal control problem (eq. 29) with a *discrete-time* CBF constraint h_QT(ξ_{i+1}) ≥ ρ·h_QT(ξ_i) along the horizon; apply the first control (receding horizon). Solved as a nonconvex SQP.
- **Layered architecture.** Mid-level MPC+CBF filter outputs velocity references → tracked by a low-level RL locomotion policy (walking policy trained in IsaacLab, domain-randomized upper-body forces). A separate QP splits the commanded heading rate ω between lower-body rotation (to RL policy) and relative upper-body/waist rotation (PD-tracked) to keep balance while reorienting.

## Key results
- Real hardware on **two platforms**: Unitree **G1 humanoid** and **Go2 quadruped**. Perception = overhead **ZED 2i** stereo → eTAM (efficient track-anything) segmentation → 2D occupancy map; pose from **OptiTrack**.
- **Dynamic collision avoidance:** dodgeball obstacles at **1.5 m/s** (quadruped) and **0.5 m/s** (humanoid). Both robots avoid via *simultaneous translation + rotation*, aligning their major axis with the predicted obstacle path to minimize translational effort. h_QT stayed positive throughout → safety maintained.
- **Environmental navigation:** teleoperated goal point through a static unstructured environment for **100 s**, humanoid carrying an oblong payload. Without geometry-aware buffering the narrow corridor is a navigational "deadlock"; the lifted safe set opens the gap by planning a reorientation (aligns lateral/major axis with corridor) and passes through.
- **Timing / compute:** numerical PDE solve (successive over-relaxation, SOR, with alternating checkerboard update for parallelism) ran **20–100 ms**; SQP (via **OSQP**) at **100 Hz**. Offboard PC: AMD Ryzen 9 9950X + RTX 4070.

## Limitations / open questions
- Boundary prediction assumes **constant obstacle velocity** over the horizon (linear advection); richer prediction models flagged by the authors as active research.
- All compute is **offboard**; PDE solve up to 100 ms and the whole pipeline depends on an **overhead camera + motion capture** — not yet onboard/egocentric perception.
- Robot modeled as a **rigid body** for the Minkowski buffering; articulated/self-manipulating geometry only gestured at as future work.
- Safety is formally a CBF guarantee only for the **single-integrator ROM**; end-to-end safety of the full-order humanoid rests on the low-level RL controller tracking "sufficiently well" (assumption, ref 33), not a proof.
- Static Poisson h₀ is a proven CBF; in the time-varying case formal guarantees are weaker due to the inherently unknown future boundary.
- No reported ablation quantifying how much conservatism the Minkowski lifting removes vs. a disk inflation (shown qualitatively as deadlock vs. pass-through).

## Concepts
- [[poisson-safety-function]]
- [[control-barrier-function]]
- [[hierarchical-control]]
- [[mapless-navigation]]
- [[rl-for-legged-locomotion]]
- [[sim-to-real-transfer]]

## My notes
This is the geometric core of the safety layer for the capability-aware G1 navigation project. The chain is exactly what we want: perception occupancy → Dirichlet BVP → CBF, with (1) moving-boundary temporal extension, (2) config-space lifting via Minkowski difference to expose orientation DOFs so the humanoid *reorients to fit* rather than inflating to a disk, (3) MPC+CBF predictive filter feeding an RL walking policy. Same hardware (G1), same lab (Ames), so it is close to a reference implementation for our stack.

Directly relevant to my open question about **exploiting the PDE structure to get ∇h and the Hessian better/cheaper than finite differences**. The paper solves the Dirichlet problem numerically via **SOR on a grid** (20–100 ms) and, as far as the text shows, treats h as a black-box field afterward — it does *not* seem to leverage the analytic structure for the gradient/Hessian used in the CBF constraint. Two facts we already have are baked into their formulation and worth pressing on:
- **trace(Hessian) = Δh = f** is *prescribed* here (they choose the superharmonic forcing f < 0). So the Laplacian of the safety function is known in closed form everywhere by construction — a hard constraint any finite-difference Hessian estimate should satisfy exactly, and a free consistency check / regularizer. Their choice of f is a design knob we could exploit (e.g. spatially shape f to control curvature).
- **On ∂Ω, ∇h aligns with the outward normal** (h = 0 level set is the obstacle boundary, and for the Dirichlet problem the gradient is normal to the level set) — so near the boundary the gradient direction is essentially free from geometry, only its magnitude needs solving.
- Open thread: because the PDE is *linear* (Poisson), ∇h and the Hessian each satisfy their own PDEs derived by differentiating Δh = f (e.g. Δ(∂h/∂x) = ∂f/∂x). One could solve for the derivative fields directly on the same grid/SOR rather than finite-differencing h, likely more accurate at the boundary layer where FD is worst and where the CBF constraint matters most. Worth prototyping against their SOR baseline and timing budget.
- Their **checkerboard SOR** already exposes the parallel structure; solving the gradient/Hessian fields concurrently on GPU could stay inside the 100 Hz budget. Also note the MPC uses a discrete-time CBF (h(ξ_{i+1}) ≥ ρ h(ξ_i)), which needs h *values* along a predicted trajectory more than exact ∇h — but the SQP linearization does want gradients, so accurate ∇h feeds convergence.

Contrast to bank on: they lift via Minkowski difference in a *lifted* config space and let q drop out of the Laplacian — elegant, but the "capability-aware" angle (which gaps the robot can actually reorient through given balance/actuation limits) is exactly the piece their rigid-body + "sufficient tracking" assumption punts on. That gap is where our contribution could sit.

## Source
arXiv:2508.11129 (v1, 15 Aug 2025) · https://arxiv.org/abs/2508.11129 · IEEE-RAS Humanoids 2025. PDF at [[attachments/@bena2025geometry.pdf]]. Video: https://youtu.be/i8uMyW4iSQw
