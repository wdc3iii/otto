---
type: paper
citekey: paszke2017automatic
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Paszke, Adam
- Gross, Sam
- Chintala, Soumith
- Chanan, Gregory
- Yang, Edward
- DeVito, Zachary
- Lin, Zeming
- Desmaison, Alban
- Antiga, Luca
- Lerer, Adam
year: 2017
venue: Neural Information Processing
doi: null
arxiv: null
url: null
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- paszke2017automatic
---

# Automatic differentiation in PyTorch

> [!info] Paszke, Adam; Gross, Sam; Chintala, Soumith; Chanan, Gregory; Yang, Edward; DeVito, Zachary · 2017 · Neural Information Processing

## Summary
> [!note] AI-drafted from this paper's well-established content (no machine-readable abstract available from OpenAlex) — a base to refine.
**TL;DR** — Describes PyTorch's automatic differentiation engine (autograd): a reverse-mode, tape-based, define-by-run system that differentiates imperative Python code executed on CPU or GPU.

**Problem** — Deep-learning frameworks of the time favored static, define-then-run computation graphs, which are awkward for models with dynamic control flow and hurt research iteration speed and debuggability.

**Method** — PyTorch builds the computation graph dynamically as operations execute ("define-by-run"), recording a tape of operations and then applying reverse-mode automatic differentiation to compute gradients. It draws on Lua Torch, Chainer, and HIPS autograd, exposing an imperative, NumPy-like API with transparent GPU acceleration.

**Key results** — Delivers automatic differentiation of arbitrary imperative programs with competitive performance, enabling rapid research iteration; the design became the foundation of the widely adopted PyTorch library.

## Takeaways
- Define-by-run dynamic graphs make gradient computation natural for models with data-dependent control flow and ease debugging.
- Reverse-mode AD over a recorded tape is the core mechanism; the API stays imperative and Pythonic.
- This is a systems/framework contribution (a NeurIPS autodiff workshop paper), not a new learning result — its value is infrastructural.

## Relevance to your work
PyTorch's autograd is the differentiation backbone for training the learned models in your pipeline (e.g. learned tracking-error bounds and policies), and its gradients feed differentiable-optimization / learning-for-control workflows such as [[@compton2025learning]].

## Concepts


## Source
- Cited by [[@compton2025dynamic]], [[@compton2025learning]]
- bibkeys: `paszke2017automatic`
