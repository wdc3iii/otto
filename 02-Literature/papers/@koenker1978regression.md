---
type: paper
citekey: koenker1978regression
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Koenker, Roger
- Bassett Jr, Gilbert
year: 1978
venue: 'Econometrica: journal of the Econometric Society'
doi: 10.2307/1913643
arxiv: null
url: https://doi.org/10.2307/1913643
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- koenker1978regression
---

# Regression quantiles

> [!info] Koenker, Roger; Bassett Jr, Gilbert · 1978 · Econometrica: journal of the Econometric Society

## Summary
> [!note] AI-drafted from the abstract and this paper's well-established content (JSTOR abstract was unavailable) — a base to refine.
**TL;DR** — Introduces regression quantiles, extending the notion of sample quantiles to the linear regression model by minimizing an asymmetrically weighted sum of absolute residuals.

**Problem** — Ordinary least squares estimates only the conditional mean and is sensitive to outliers and heteroscedasticity; there was no principled analogue of order statistics / quantiles for the linear model.

**Method** — Define the θ-th regression quantile as the parameter vector minimizing a sum of residuals weighted asymmetrically by θ for positive residuals and (1−θ) for negative ones — the "check" (pinball) loss. The estimator generalizes the median regression (least absolute deviations) case and can be computed via linear programming; the paper develops its statistical properties (existence, uniqueness, equivariance, and asymptotic behavior).

**Key results** — Establishes regression quantiles as a natural, robust generalization of order statistics to regression, with a full characterization of their algebraic and distributional properties.

## Takeaways
- The asymmetric pinball loss is the foundational tool for estimating conditional quantiles rather than means — directly usable as a training objective for learning tail/quantile bounds.
- Robust to outliers and captures the full conditional distribution (heteroscedasticity), not just its center.
- A classical econometrics/statistics result; the enduring practical export to ML is the quantile (pinball) loss.

## Relevance to your work
The quantile (pinball) loss from this paper is the statistical machinery for learning a probabilistic tracking-error bound: fitting a chosen quantile of the tracking error gives a data-driven, calibrated envelope rather than a worst-case one, connecting to [[@compton2025learning]].

## Concepts
[[tracking-error-bound]]

## Source
- Cited by [[@compton2025dynamic]], [[@compton2025learning]]
- bibkeys: `koenker1978regression`
