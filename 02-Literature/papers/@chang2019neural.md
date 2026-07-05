---
type: paper
citekey: chang2019neural
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Chang, Ya-Chien
- Roohi, Nima
- Gao, Sicun
year: 2019
venue: Advances in neural information processing systems
doi: null
arxiv: '2005.00611'
url: https://arxiv.org/abs/2005.00611
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@chang2019neural.pdf
bibkeys:
- Chang2020
---

# Neural lyapunov control

> [!info] Chang, Ya-Chien; Roohi, Nima; Gao, Sicun · 2019 · Advances in neural information processing systems

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A learner-falsifier framework that jointly learns a control policy and a neural-network Lyapunov function for nonlinear systems, with formal stability guarantees and larger regions of attraction than LQR or SOS/SDP.
**Problem** — Designing a controller together with a Lyapunov certificate for nonlinear systems is hard; classical methods (LQR linearization, SOS/SDP) are either local or scale poorly, and learned controllers usually lack stability proofs.
**Method** — A learner trains a neural Lyapunov function and a control policy to satisfy the Lyapunov decrease conditions over the domain; a falsifier (an SMT/counterexample search, e.g., dReal) then searches for states violating the conditions. Counterexamples are fed back to the learner, and the loop repeats until the falsifier can find no violation — at which point the certificate is formally valid.
**Key results** — Yields provably stable controllers with regions of attraction significantly larger than those from LQR and SOS/SDP baselines on nonlinear control benchmarks.

## Takeaways
- The formal guarantee is the differentiator: the falsifier turns a learned Lyapunov function into a *verified* certificate, not just an empirically good one.
- Co-designing controller and Lyapunov function enlarges the certified region of attraction versus fixing one and solving for the other.
- Scalability is bounded by the falsifier (SMT over the state space), so it targets low-dimensional nonlinear systems rather than high-DOF robots directly.

## Relevance to your work
Learning-plus-verification of Lyapunov certificates connects to certified-stability arguments for learned locomotion/control policies; a natural reference point for the stability-certificate framing in [[@compton2025dynamic]].

## Concepts


## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `Chang2020`
