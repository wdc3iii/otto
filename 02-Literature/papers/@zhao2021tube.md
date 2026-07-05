---
type: paper
citekey: zhao2021tube
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Pan Zhao
- Arun Lakshmanan
- Kasey Ackerman
- Aditya Gahlawat
- Marco Pavone
- Naira Hovakimyan
year: 2021
venue: IEEE Robotics and Automation Letters
doi: null
arxiv: '2109.04453'
url: https://arxiv.org/abs/2109.04453
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@zhao2021tube.pdf
bibkeys:
- Zhao2021
---

# Tube-Certified Trajectory Tracking for Nonlinear Systems With Robust Control Contraction Metrics

> [!info] Pan Zhao; Arun Lakshmanan; Kasey Ackerman; Aditya Gahlawat; Marco Pavone; Naira Hovakimyan · 2021 · IEEE Robotics and Automation Letters

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — Robust Control Contraction Metrics (RCCM) that directly minimize the L-infinity gain from disturbances to trajectory deviation, yielding tighter certified tracking tubes than standard CCM+ISS analysis.

**Problem** — Guaranteed trajectory tracking for disturbed nonlinear control-affine systems requires invariant tubes; existing CCM-based tubes (via input-to-state stability) are conservative.

**Method** — The controller and metric are synthesized to minimize the L-infinity gain from disturbance to nominal-actual deviation. Tubes are computed offline and hold for any nominal trajectory. Under mild assumptions the authors prove RCCM tubes are tighter than the CCM+ISS baseline, and integrate the RCCM tracking controller + tubes into a feedback motion-planning framework.

**Key results** — Simulations show tighter tubes / reduced conservatism versus the CCM-based approach, and safe planned trajectories using the tube certificates.

## Takeaways
- Optimizing the L-infinity disturbance-to-deviation gain (rather than settling for an ISS bound) is the lever that tightens the tube.
- Tubes are trajectory-independent and precomputed offline — cheap to reuse across nominal plans in a planner.
- Guarantees rest on the control-affine + contraction-metric structure and disturbance bounds.

## Relevance to your work
This is a core contraction-metric route to certified tracking tubes for feedback motion planning; it is a direct methodological precursor to dynamic-tube tracking as developed in [[@compton2025dynamic]].

## Abstract (from bib)
This paper presents an approach towards guaranteed trajectory tracking for nonlinear control-affine systems subject to external disturbances based on robust control contraction metrics (CCM) that aims to minimize the $\mathcal L_\infty$ gain from the disturbances to nominal-actual trajectory deviations. The guarantee is in the form of invariant tubes, computed offline and valid for any nominal trajectories, in which the actual states and inputs of the system are guaranteed to stay despite disturbances. Under mild assumptions, we prove that the proposed robust CCM (RCCM) approach yields tighter tubes than an existing approach based on CCM and input-to-state stability analysis. We show how the RCCM-based tracking controller together with tubes can be incorporated into a feedback motion plann

## Concepts
[[tube-mpc]] [[tracking-error-bound]] [[dynamic-tube]]

## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `Zhao2021`
