---
type: paper
citekey: neunert2018whole
tags: [control, locomotion]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Neunert, Michael
- Stäuble, Markus
- Giftthaler, Markus
- Bellicoso, Carmine D.
- Carius, Jan
- Gehring, Christian
- Hutter, Marco
- Buchli, Jonas
year: 2018
venue: IEEE Robotics and Automation Letters
doi: 10.1109/LRA.2018.2800124
arxiv: '1712.02889'
url: http://arxiv.org/abs/1712.02889
zotero: null
summary: ai-draft
pdf: attachments/@neunert2018whole.pdf
status: to-read
mine: false
bibkeys:
- neunertWholeBodyNonlinearModel2018
---

# Whole-Body Nonlinear Model Predictive Control Through Contacts for Quadrupeds

> [!info] Michael Neunert; Markus Stäuble; Markus Giftthaler; Carmine D. Bellicoso; Jan Carius; Christian Gehring; Marco Hutter; Jonas Buchli · 2018 · IEEE Robotics and Automation Letters

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A whole-body nonlinear MPC that uses the full dynamic model with explicit contact dynamics, so contact locations/sequences/timings are optimized (not prespecified), running up to 190 Hz on a quadruped.
**Problem** — Controlling rigid-body systems subject to contacts without prespecifying contact schedules, while staying fast enough for real-time whole-body control.
**Method** — Whole-body nonlinear MPC over a full dynamic system model including explicit contact dynamics; the optimal-control solver optimizes contact locations, sequences, and timings; heavy numerical and software engineering to run the solver online.
**Key results** — Runs at rates up to 190 Hz on a quadruped over a 0.5 s horizon — reported as outperforming the state of the art by at least an order of magnitude; hardware experiments (periodic and non-periodic tasks) on two quadrupeds with different actuation systems demonstrate performance, transferability, and robustness.

## Takeaways
- Contact-implicit whole-body NMPC: contact schedule emerges from optimization rather than a fixed gait/contact plan.
- Full-dynamics model with explicit contact dynamics, not a reduced-order surrogate.
- Real-time (up to 190 Hz, 0.5 s horizon) validated on two differently-actuated quadrupeds.

## Relevance to your work
Squarely in your classical control line: a whole-body contact-implicit NMPC formulation for legged robots, a key data point on the full-dynamics end of the MPC spectrum (contrast with reduced-order/tube-MPC approaches you use), and from the Hutter/Buchli lineage relevant to your G1 planning-and-control stack.

## Abstract (from bib)
In this work we present a whole-body Nonlinear Model Predictive Control approach for Rigid Body Systems subject to contacts. We use a full dynamic system model which also includes explicit contact dynamics. Therefore, contact locations, sequences and timings are not prespecified but optimized by the solver. Yet, thorough numerical and software engineering allows for running the nonlinear Optimal Control solver at rates up to 190 Hz on a quadruped for a time horizon of half a second. This outperforms the state of the art by at least one order of magnitude. Hardware experiments in form of periodic and non-periodic tasks are applied to two quadrupeds with different actuation systems. The obtained results underline the performance, transferability and robustness of the approach.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- bibkeys: `neunertWholeBodyNonlinearModel2018`
- arXiv: http://arxiv.org/abs/1712.02889
- DOI: https://doi.org/10.1109/LRA.2018.2800124
- URL: http://arxiv.org/abs/1712.02889
