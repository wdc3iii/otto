---
type: paper
citekey: huber1992robust
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Huber, Peter J
year: 1992
venue: 'Breakthroughs in statistics: Methodology and distribution'
doi: 10.1007/978-1-4612-4380-9_35
arxiv: null
url: https://doi.org/10.1007/978-1-4612-4380-9_35
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- huber1992robust
---

# Robust estimation of a location parameter

> [!info] Huber, Peter J · 1992 · Breakthroughs in statistics: Methodology and distribution

## Summary
> [!note] AI-drafted from the bibliographic record (no abstract was available; original: Huber, Ann. Math. Statist. 1964, reprinted 1992) — a base to refine.

**TL;DR** — Huber's foundational paper on robust statistics: it formalizes M-estimators for a location parameter and derives an estimator (the Huber estimator/loss) that is minimax-optimal for a contaminated-Gaussian neighborhood, guarding against outliers.

**Problem** — Classical estimators are non-robust: the sample mean (L2/least-squares) is efficient under Gaussian noise but highly sensitive to outliers, while the median (L1) is robust but less efficient; a location estimator is needed that degrades gracefully under distributional contamination.

**Method** — Generalizes maximum-likelihood estimation to M-estimation (minimizing a sum of a robust loss ρ, equivalently solving an estimating equation with influence function ψ), and studies estimators over an ε-contamination neighborhood of the Gaussian, deriving the minimax choice — the Huber loss that is quadratic near zero and linear in the tails.

**Key results** — Establishes the Huber M-estimator as a minimax-robust compromise between the mean and the median, launching the theory of robust estimation. (Specific theorems not restated here — no abstract was fetched.)

## Takeaways
- Origin of the Huber loss: quadratic for small residuals, linear for large ones — the canonical robust-regression loss.
- Introduces M-estimators and the ε-contamination minimax framing that underpins modern robust statistics.
- The tuning point at which quadratic switches to linear sets the efficiency-vs-robustness trade-off.

## Relevance to your work
The source of the Huber loss commonly used to make regression/learning objectives (e.g., learned dynamics or tube models) robust to outliers and heavy tails. See [[@compton2025dynamic]].

## Concepts


## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `huber1992robust`
