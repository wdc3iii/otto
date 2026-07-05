---
type: paper
citekey: salzmann2023real
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Salzmann, Tim
- Kaufmann, Elia
- Arrizabalaga, Jon
- Pavone, Marco
- Scaramuzza, Davide
- Ryll, Markus
year: 2023
venue: IEEE Robotics and Automation Letters
doi: 10.1109/LRA.2023.3246839
arxiv: '2203.07747'
url: https://doi.org/10.1109/LRA.2023.3246839
summary: ai-draft
pdf: attachments/@salzmann2023real.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- salzmann2023neural
---

# Real-time Neural-MPC: Deep Learning Model Predictive Control for Quadrotors and Agile Robotic Platforms

> [!info] Salzmann, Tim; Kaufmann, Elia; Arrizabalaga, Jon; Pavone, Marco; Scaramuzza, Davide; Ryll, Markus · 2023 · IEEE Robotics and Automation Letters

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A framework for embedding large neural-network dynamics models inside a gradient-based online-optimization MPC loop while retaining real-time (50 Hz) operation on embedded hardware.

**Problem** — MPC control quality hinges on an accurate dynamics model, but embedded real-time loops have historically been restricted to simple first-principle models; expressive neural network models were too computationally heavy to fit in the real-time iteration.

**Method** — Real-time Neural MPC efficiently integrates large, complex neural-network architectures as the dynamics model within a gradient-based online-optimization MPC pipeline, so learned models can be evaluated and differentiated inside the fast iteration loop on embedded platforms.

**Key results** — Runs learned dynamics with over 4000× larger parametric capacity than prior online-optimization-MPC neural integrations within a 50 Hz real-time window on embedded hardware; on a real agile quadrotor it reduces positional tracking error by up to 82% versus state-of-the-art MPC without neural dynamics.

## Takeaways
- Makes high-capacity learned dynamics compatible with fast gradient-based MPC, not just with sampling-based or offline schemes.
- The 82% tracking-error reduction on real hardware shows model expressiveness materially improves closed-loop performance for agile flight.
- Targets gradient-based online-optimization MPC specifically; the enabling contribution is the efficient integration/AD of the network into the solver's real-time loop.

## Relevance to your work
A concrete precedent for putting learned models inside a real-time gradient-based MPC solver — directly relevant to integrating learned dynamics/error models into your predictive controllers, as in [[@compton2025dynamic]].

## Concepts


## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `salzmann2023neural`
- DOI: https://doi.org/10.1109/LRA.2023.3246839
