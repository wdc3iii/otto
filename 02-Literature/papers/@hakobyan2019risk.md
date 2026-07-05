---
type: paper
citekey: hakobyan2019risk
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Hakobyan, Astghik
- Kim, Gyeong Chan
- Yang, Insoon
year: 2019
venue: IEEE Robotics and Automation Letters
doi: 10.1109/LRA.2019.2929980
arxiv: null
url: https://doi.org/10.1109/LRA.2019.2929980
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- hakobyan2019
---

# Risk-Aware Motion Planning and Control Using CVaR-Constrained Optimization

> [!info] Hakobyan, Astghik; Kim, Gyeong Chan; Yang, Insoon · 2019 · IEEE Robotics and Automation Letters

## Summary
> [!note] AI-drafted from the abstract — a base to refine.

**TL;DR** — A two-stage risk-aware motion planning and control method that uses conditional value-at-risk (CVaR) constraints in a receding-horizon controller to systematically trade off safety and conservativeness among randomly moving obstacles.

**Problem** — Planning safely in environments with randomly moving obstacles while tuning conservativeness; chance constraints are not coherent/convex and ignore tail severity, whereas CVaR is coherent, convex, and distinguishes tail events.

**Method** — Stage 1 generates a reference trajectory via RRT*. Stage 2 uses a receding-horizon controller with CVaR constraints to bound safety risk. Because the CVaR-constrained problem is a triple-level stochastic program, it is made tractable via (1) a reformulation of the CVaR constraints, (2) sample average approximation, and (3) a linearly-constrained mixed-integer convex program formulation.

**Key results** — Demonstrated in simulation using a 12-dimensional quadrotor model, showing tunable risk-vs-conservativeness behavior.

## Takeaways
- CVaR is the risk measure of choice: coherent and convex, and unlike chance constraints it accounts for the magnitude of tail (collision) events.
- Decouples planning (RRT*) from risk-bounded tracking (receding-horizon CVaR control).
- Tractability hinges on reformulation + sample average approximation + a MICP encoding.

## Relevance to your work
A principled framework for encoding risk (CVaR) into receding-horizon control under stochastic obstacles — relevant to risk-sensitive safety filtering and comparison with CBF-based approaches. See [[@compton2025dynamic]].

## Concepts


## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `hakobyan2019`
- DOI: https://doi.org/10.1109/LRA.2019.2929980
