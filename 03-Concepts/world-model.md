---
type: concept
tags: [rl, method, to-revisit]
aliases: [World model, learned dynamics model, latent dynamics]
created: 2026-07-26
modified: 2026-07-26
---

# World model

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
A **learned model of environment dynamics** — often in a compact latent space — that an agent uses to predict future observations/rewards and to plan or train a policy "in imagination" rather than only from real interaction ([[@ha2018world]], [[@hafner2023mastering]]).

## Intuition / why it matters
World models buy **sample efficiency** and enable planning by rolling out a learned simulator internally. This is the learned-model counterpart to the analytic dynamics / [[reduced-order-model|ROM]] models I use in MPC — the interesting tension is *when a learned latent model beats an analytic one* for contact-rich legged dynamics.

## Grounding
- Origin: [[@ha2018world]] (World Models — VAE + RNN, "dream" training).
- Scaled/general: [[@hafner2023mastering]] (DreamerV3, one config across 150+ tasks).
- Foundation world model: [[@bruce2024genie]] (Genie — action-controllable environments from video).

## Related
- [[foundation-model]]

## Open questions
- Fidelity of learned world models for **contact-rich, discontinuous** legged dynamics.
- Learned latent dynamics vs. analytic ROM/MPC — which wins where, and can they be composed?
