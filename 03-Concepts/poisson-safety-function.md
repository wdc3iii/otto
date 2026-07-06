---
type: concept
tags: [control, navigation, to-revisit]
aliases: [Poisson safety function, PSF]
created: 2026-07-06
modified: 2026-07-06
---

# Poisson safety function

> [!note] Stub — expand when revisited.

## Definition
A control barrier function synthesized **numerically** by solving a Dirichlet boundary-value problem for Poisson's equation over the free-space domain $\Omega$:
$$\Delta h_0(y)=f(y)\ \forall y\in\Omega,\qquad h_0(y)=0\ \forall y\in\partial\Omega,$$
with smooth strictly-negative forcing $f$ making $h_0$ superharmonic. The zero-superlevel set of $h_0$ defines the safe set **directly from perception occupancy** — no analytic obstacle primitives or SDF. $h_0$ is a valid CBF for single-integrator dynamics. See [[control-barrier-function]].

## Why it matters
Gets a smooth, provably-safe set straight from an occupancy grid, and its PDE structure exposes useful facts: $\mathrm{trace(Hessian)}=\Delta h=f$ (one diagonal entry free), and on $\partial\Omega$ the gradient aligns with the outward surface normal — the hooks behind the [[capability-aware-navigation]] project's $\nabla h$/Hessian efficiency question.

## Grounding
- [[@bena2025geometry]] — PSF + moving-boundary + configuration-space lifting + MPC-CBF filter.
- [[@yang2026safesage]] — Laplace-modulated PSF for semantic/social safety.

## See also
[[control-barrier-function]] · [[social-navigation]] · [[capability-aware-navigation]]
