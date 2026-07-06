---
type: paper
citekey: compton2025learning
tags: [control, rl]
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Compton, William D.
- Cohen, Max H.
- Ames, Aaron D.
year: 2025
venue: L4DC 2025 (PMLR 283)
doi: null
arxiv: '2412.04658'
url: https://arxiv.org/abs/2412.04658
authorship: first
zotero: null
status: read
mine: true
summary: ai-draft
pdf: attachments/@compton2025learning.pdf
---

# Learning for Layered Safety-Critical Control with Predictive Control Barrier Functions

> [!info] Compton, William D.; Cohen, Max H.; Ames, Aaron D. · 2025 · L4DC 2025 (PMLR 283) — **my paper**

## Abstract
Safety filters leveraging control barrier functions (CBFs) are highly effective for enforcing safe behavior on complex systems. It is often easier to synthesize CBFs for a Reduced order Model (RoM), and track the resulting safe behavior on the Full order Model (FoM)—yet gaps between the RoM and FoM can result in safety violations. This paper introduces predictive CBFs to ad- dress this gap by leveraging rollouts of the FoM to define a predictive robustness term added to the RoM CBF condition. Theoretically, we prove that this guarantees safety in a layered control imple- mentation. Practically, we learn the predictive robustness term through massive parallel simulation with domain randomization. We demonstrate in simulation that this yields safe FoM behavior with minimal conservatism, and experimentally realize predictive CBFs on a 3D hopping robot.

## Summary
> [!note] AI-drafted from the abstract/intro — a base to refine or replace with your own framing.

**TL;DR** — Introduces **predictive CBFs**: synthesize a CBF on a reduced-order model, then add a *predictive robustness term* — learned from full-order-model rollouts — to the RoM CBF condition so the tracked behavior is provably safe on the full system.
**Problem** — CBFs are easier to build on a RoM and track on the FoM, but the RoM↔FoM gap can cause safety violations; constructive CBF synthesis for high-dim systems is largely open.
**Method** — Define a predictive robustness term from FoM rollouts, added to the RoM CBF condition; prove it guarantees safety in a layered implementation; **learn** the term via massively parallel simulation with domain randomization.
**Key results** — Sim: safe FoM behavior with minimal conservatism. Hardware: predictive CBFs realized on a **3D hopping robot**.

## Takeaways
- A learned, prediction-based robustification of the RoM→FoM safety transfer — less conservative than worst-case margins.
- Same recipe family as DTMPC (learn a robustification term from parallel sim), but for CBF safety filters rather than tube MPC.

## Where it sits in my work
Sits beside [[@compton2025dynamic|DTMPC]] (learned robustness from parallel sim, layered safety) and [[@cohen2025safety|ROM+CBF synthesis]] (the ROM-CBF theory it robustifies); a layer of [[@hierarchies2025motion]].

## Concepts
- [[control-barrier-function]] · [[reduced-order-model]] · [[tracking-error-bound]] · [[massively-parallel-simulation]]

## References (in otto)
- [[@ames2014barrier]]
- [[@ames2016barrier]]
- [[@ames2019barrier]]
- [[@breeden2022predictive]]
- [[@chen2021backup]]
- [[@chen2021fastrack]]
- [[@cohen2024safety]]
- [[@compton2024dynamic]]
- [[@compton2024experiment]]
- [[@compton2024learning]]
- [[@csomayshanklin2021episodic]]
- [[@csomayshanklin2023nonlinear]]
- [[@csomayshanklin2024robust]]
- [[@diehl2002efficient]]
- [[@diehl2005real]]
- [[@glotfelter2017nonsmooth]]
- [[@koenker1978regression]]
- [[@langson2004robust]]
- [[@makoviychuk2021isaac]]
- [[@matni2024quantitative]]
- [[@mitchell2005time]]
- [[@molnar2022model]]
- [[@nguyen2016exponential]]
- [[@paszke2017automatic]]
- [[@raibert1984experiments]]
- [[@robey2020learning]]
- [[@schweidel2022safe]]
- [[@singh2023robust]]
- [[@singletary2021comparative]]
- [[@singletary2022safety]]
- [[@taylor2020barrier]]
- [[@tonkens2022refining]]
- [[@wabersich2022predictive]]
- [[@wabersich2023data]]
- [[@wang2017safe]]
- [[@xu2015robustness]]
