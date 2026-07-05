---
type: paper
citekey: bradbury2018jax
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Bradbury, James
- Frostig, Roy
- Hawkins, Peter
- Johnson, Matthew James
- Leary, Chris
- Maclaurin, Dougal
- Necula, George
- Paszke, Adam
- VanderPlas, Jake
- Wanderman-Milne, Skye
- Zhang, Qiao
year: 2018
venue: 'GitHub. Note: https://github.com/google/jax'
doi: null
arxiv: null
url: https://github.com/jax-ml/jax
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- jax2018github
---

# JAX: Composable transformations of Python+NumPy programs

> [!info] Bradbury, James; Frostig, Roy; Hawkins, Peter; Johnson, Matthew James; Leary, Chris; Maclaurin, Dougal · 2018 · GitHub. Note: https://github.com/google/jax

## Summary
> [!note] AI-drafted from the project README (no abstract) — a base to refine.
**TL;DR** — JAX is a Python library for accelerator-oriented array computation and composable program transformations, pairing NumPy-style code with automatic differentiation and XLA compilation.
**Problem** — High-performance numerical computing and large-scale ML need automatic differentiation, JIT compilation, and hardware acceleration over ordinary Python/NumPy code without rewriting it.
**Method** — JAX automatically differentiates native Python and NumPy functions (through loops, branches, recursion, closures; reverse- and forward-mode, composable to arbitrary order via `jax.grad`), and uses XLA to compile and scale programs on TPUs, GPUs, and other accelerators (`jax.jit`). It is fundamentally an extensible system of composable function transformations (grad, jit, vmap, pmap) at scale.
**Key results** — A widely adopted research tool; transformations compose arbitrarily, enabling differentiable, vectorized, and parallelized numerical programs.

## Takeaways
- Software/tooling citation, not a research result: the value is composable `grad`/`jit`/`vmap` and XLA acceleration.
- Enables differentiable simulation and GPU/TPU-parallel batched computation, which is why planning and RL pipelines cite it.
- Functional/pure-function programming model is a design constraint (and the source of its "sharp edges").

## Relevance to your work
Cited as the computational substrate for differentiable, GPU-parallelized planning and control pipelines — e.g. the sampling/optimization machinery in robust motion planning. See [[@csomayshanklin2024robust]].

## Concepts


## Source
- Cited by [[@csomayshanklin2024robust]], [[@hierarchies2025motion]]
- bibkeys: `jax2018github`
