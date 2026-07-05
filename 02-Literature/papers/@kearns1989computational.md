---
type: paper
citekey: kearns1989computational
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- M. J. Kearns
year: 1989
venue: null
doi: null
arxiv: null
url: https://www.cis.upenn.edu/~mkearns/papers/thesis.pdf
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@kearns1989computational.pdf
bibkeys:
- kearns89
---

# Computational Complexity of Machine Learning

> [!info] M. J. Kearns · 1989 · —

## Summary
> [!note] AI-drafted from public metadata/abstract of the thesis — a base to refine.
**TL;DR** — Kearns's ACM-Distinguished PhD thesis: a foundational study of when concept classes are efficiently learnable in Valiant's distribution-free (PAC) model, including hardness results and sample-complexity lower bounds.
**Problem** — Characterize the computational (not just statistical) feasibility of learning from examples: which concept classes admit polynomial-time learning algorithms, and which are intractable?
**Method** — Works within the PAC framework; develops general tools for establishing polynomial-time learnability, studies learning under noisy examples, and proves hardness by reducing cryptographic / number-theoretic problems to learning problems.
**Key results** — Demonstrates the computational difficulty of learning several well-studied classes (Boolean formulae, DFAs, a simplified form of neural networks), gives lower bounds on the number of examples required, and treats efficient learning in the presence of errors. (Later revised as an MIT Press monograph, 1990.)

## Takeaways
- Cornerstone of computational learning theory: separates statistical learnability from computational tractability.
- Cryptographic reductions give strong evidence that certain natural concept classes are not efficiently PAC-learnable.
- A theory-of-learning reference rather than a control/robotics result; likely cited for learnability/sample-complexity framing.

## Relevance to your work
Provides the computational-learning-theory backdrop (PAC learnability, sample-complexity lower bounds) that a learning-based control paper draws on when reasoning about what is and is not efficiently learnable.

## Concepts


## Source
- Cited by [[@compton2024constructive]]
- bibkeys: `kearns89`
