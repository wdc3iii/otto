---
type: paper
citekey: gibson2023multi
tags: [control, method, planning]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Gibson, Jason
- Vlahov, Bogdan
- Fan, David
- Spieler, Patrick
- Pastor, Daniel
- Agha-mohammadi, Ali-akbar
- Theodorou, Evangelos A.
year: 2023
venue: arXiv
doi: 10.48550/arXiv.2305.02241
arxiv: '2305.02241'
url: http://arxiv.org/abs/2305.02241
zotero: null
summary: ai-draft
pdf: attachments/@gibson2023multi.pdf
status: to-read
mine: false
bibkeys:
- gibsonMultistepDynamicsModeling2023
---

# A Multi-step Dynamics Modeling Framework For Autonomous Driving In Multiple Environments

> [!info] Jason Gibson; Bogdan Vlahov; David Fan; Patrick Spieler; Daniel Pastor; Ali-akbar Agha-mohammadi; Evangelos A. Theodorou · 2023 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A hybrid multi-step dynamics-prediction framework using a fixed-horizon LSTM that explicitly handles modeling-error accumulation and scales for sampling-based control of an off-road all-terrain vehicle.
**Problem** — Off-road vehicles face highly complex, hard-to-model terrain/vehicle interactions plus complex vehicle dynamics, challenging high-speed control and planning.
**Method** — A hybrid model combining a specially-initialized LSTM (predicting only over a limited/fixed time horizon, avoiding the long-term stability problems of RNN training) with a physics component; requires only odometry information for labels; designed to stay scalable for sampling-based controllers.
**Key results** — Predicts millions of possible trajectories in real-time over a 5-second horizon in challenging off-road driving; validated on a Polaris S4 1000 RZR in two distinct environments (no other numeric figures read).

## Takeaways
- Bounding the LSTM to a fixed prediction horizon sidesteps long-horizon RNN instability while a physics prior carries the rest.
- Odometry-only labels make the approach cheap to train; scalability enables massive parallel trajectory rollouts for sampling-based (MPPI-style) control.

## Relevance to your work
Tangential platform (off-road wheeled vehicles), but the hybrid learned+physics dynamics model feeding a sampling-based controller is methodologically relevant to reduced-order / learned-dynamics MPC for legged systems — especially the treatment of multi-step model-error accumulation.

## Abstract (from bib)
Modeling dynamics is often the first step to making a vehicle autonomous. While on-road autonomous vehicles have been extensively studied, off-road vehicles pose many challenging modeling problems. An off-road vehicle encounters highly complex and difficult-to-model terrain/vehicle interactions, as well as having complex vehicle dynamics of its own. These complexities can create challenges for effective high-speed control and planning. In this paper, we introduce a framework for multistep dynamics prediction that explicitly handles the accumulation of modeling error and remains scalable for sampling-based controllers. Our method uses a specially-initialized Long Short-Term Memory (LSTM) over a limited time horizon as the learned component in a hybrid model to predict the dynamics of a 4-person seating all-terrain vehicle (Polaris S4 1000 RZR) in two distinct environments. By only having the LSTM predict over a fixed time horizon, we negate the need for long term stability that is often a challenge when training recurrent neural networks. Our framework is flexible as it only requires odometry information for labels. Through extensive experimentation, we show that our method is able to predict millions of possible trajectories in real-time, with a time horizon of five seconds in challenging off road driving scenarios.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- bibkeys: `gibsonMultistepDynamicsModeling2023`
- arXiv: http://arxiv.org/abs/2305.02241
- DOI: https://doi.org/10.48550/arXiv.2305.02241
- URL: http://arxiv.org/abs/2305.02241
