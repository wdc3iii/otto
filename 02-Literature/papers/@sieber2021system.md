---
type: paper
citekey: sieber2021system
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Jerome Sieber
- Samir Bennani
- Melanie N. Zeilinger
year: 2021
venue: IEEE Control Systems Letters
doi: null
arxiv: '2103.02460'
url: https://arxiv.org/abs/2103.02460
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@sieber2021system.pdf
bibkeys:
- Sieber2021
---

# A System Level Approach to Tube-based Model Predictive Control

> [!info] Jerome Sieber; Samir Bennani; Melanie N. Zeilinger · 2021 · IEEE Control Systems Letters

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — A tube-MPC formulation built on the System Level Parameterization (SLP) that optimizes the tube (ancillary) controller online instead of fixing it a priori, cutting conservativeness.

**Problem** — Classical robust tube-MPC tightens constraints using an a-priori-fixed tube controller; that fixed choice is conservative because the tube geometry cannot adapt during the online optimization.

**Method** — The authors establish an equivalence between a class of robust MPC methods and the SLP, then derive System Level Tube-MPC (SLTMPC), in which the tube controller becomes a decision variable co-optimized with the nominal trajectory. SLTMPC is shown to arise naturally from an extended SLP formulation.

**Key results** — A numerical example demonstrates reduced conservativeness relative to fixed-tube robust MPC.

## Takeaways
- Key idea: make the tube/ancillary feedback a decision variable rather than a fixed pre-computed gain — the tube adapts to the current problem.
- The robust-MPC ↔ SLP equivalence is the conceptual bridge that makes this clean.
- Linear/constrained setting with a numerical (not hardware) validation.

## Relevance to your work
Directly relevant to dynamic-tube MPC: it is a concrete mechanism for online co-design of the tube instead of a conservative fixed cross-section, motivating work like [[@compton2025dynamic]].

## Abstract (from bib)
Robust tube-based model predictive control (MPC) methods address constraint satisfaction by leveraging an a priori determined tube controller in the prediction to tighten the constraints. This paper presents a system level tube-MPC (SLTMPC) method derived from the system level parameterization (SLP), which allows optimization over the tube controller online when solving the MPC problem, which can significantly reduce conservativeness. We derive the SLTMPC method by establishing an equivalence relation between a class of robust MPC methods and the SLP. Finally, we show that the SLTMPC formulation naturally arises from an extended SLP formulation and show its merits in a numerical example.

## Concepts
[[tube-mpc]] [[dynamic-tube]]

## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `Sieber2021`
