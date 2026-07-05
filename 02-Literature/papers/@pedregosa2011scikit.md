---
type: paper
citekey: pedregosa2011scikit
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Pedregosa, Fabian
- Varoquaux, Gaël
- Gramfort, Alexandre
- Michel, Vincent
- Thirion, Bertrand
- Grisel, Olivier
- Blondel, Mathieu
- Prettenhofer, Peter
- Weiss, Ron
- Dubourg, Vincent
- Vanderplas, Jake
- Passos, Alexandre
year: 2011
venue: Journal of Machine Learning Research
doi: 10.48550/arxiv.1201.0490
arxiv: 1201.0490
url: https://arxiv.org/abs/1201.0490
summary: ai-draft
pdf: attachments/@pedregosa2011scikit.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- scikit-learn
---

# Scikit-learn: Machine Learning in Python

> [!info] Pedregosa, Fabian; Varoquaux, Gaël; Gramfort, Alexandre; Michel, Vincent; Thirion, Bertrand; Grisel, Olivier · 2011 · Journal of Machine Learning Research

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Introduces scikit-learn, a general-purpose Python library exposing a wide range of state-of-the-art supervised and unsupervised machine-learning algorithms through a uniform, dependency-light API.
**Problem** — Bringing machine learning to non-specialists required a package that was easy to use, well-documented, and performant without forcing users into a specialized language or heavy dependencies.
**Method** — The library integrates classic ML algorithms (SVMs, linear models, clustering, dimensionality reduction, model selection, preprocessing) behind a consistent estimator interface, built on NumPy/SciPy with performance-critical parts in Cython, distributed under a permissive BSD license.
**Key results** — Establishes a widely adopted, well-tested reference implementation emphasizing ease of use, documentation, and API consistency for medium-scale problems.

## Takeaways
- The value is engineering and API design, not a new algorithm: a uniform `fit`/`predict` estimator interface over many methods.
- Targeted at medium-scale problems on a single machine; not a deep-learning or distributed framework.
- BSD-licensed and broadly used, which is why it appears as tooling in empirical robotics/ML pipelines.

## Relevance to your work
A utility citation: locomotion/control pipelines lean on scikit-learn for offline data analysis, regression/classification, and dimensionality reduction around policy training and system-identification workflows such as those in [[@hierarchies2025motion]].

## Concepts


## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `scikit-learn`
