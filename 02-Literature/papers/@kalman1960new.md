---
type: paper
citekey: kalman1960new
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Kalman, R. E.
year: 1960
venue: Journal of Basic Engineering
doi: 10.1115/1.3662552
arxiv: null
url: https://doi.org/10.1115/1.3662552
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- kalman_new_1960
---

# A New Approach to Linear Filtering and Prediction Problems

> [!info] Kalman, R. E. · 1960 · Journal of Basic Engineering

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — The paper that introduced the (discrete-time) Kalman filter: a recursive, state-space solution to the linear filtering and prediction problem.
**Problem** — The classical Wiener filtering/prediction problem was limited to stationary statistics and spectral methods; a general recursive solution handling nonstationary and finite/infinite-memory settings was needed.
**Method** — Recasts filtering in state-space using the Bode-Shannon representation of random processes and the state-transition method; derives a nonlinear (Riccati) difference/differential equation for the covariance of the optimal estimation error, from which the optimal linear filter's coefficients follow directly.
**Key results** — A single recursive formulation applies to stationary and nonstationary statistics and to growing- and infinite-memory filters; shows the filtering problem is the dual of the noise-free (LQ) regulator problem.

## Takeaways
- Founding result of modern state-space estimation; the error-covariance Riccati recursion is its computational heart.
- The estimation/control duality (filter <-> regulator) is a recurring structural theme in optimal control.
- Optimality is for linear systems with the stated noise assumptions; nonlinear/robust extensions came later.

## Relevance to your work
State estimation is the perception layer feeding any locomotion controller; the Kalman filter and its LQ/regulator duality are baseline machinery, cited in [[@compton2024constructive]] as classical optimal-estimation/control foundations.

## Abstract (from bib)
The classical filtering and prediction problem is re-examined using the Bode-Shannon representation of random processes and the “state-transition” method of analysis of dynamic systems. New results are: (1) The formulation and methods of solution of the problem apply without modification to stationary and nonstationary statistics and to growing-memory and infinite-memory filters. (2) A nonlinear difference (or differential) equation is derived for the covariance matrix of the optimal estimation error. From the solution of this equation the co-efficients of the difference (or differential) equation of the optimal linear filter are obtained without further calculations. (3) The filtering problem is shown to be the dual of the noise-free regulator problem. The new method developed here is app

## Concepts


## Source
- Cited by [[@compton2024constructive]]
- bibkeys: `kalman_new_1960`
- DOI: https://doi.org/10.1115/1.3662552
- URL: https://doi.org/10.1115/1.3662552
