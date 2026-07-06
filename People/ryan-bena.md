---
type: person
tags: [control, navigation, hardware]
aliases: [Ryan Bena, Ryan M. Bena]
affiliation: Caltech — AMBER Lab (Aaron D. Ames)
role: Postdoctoral Scholar
homepage:
scholar: https://scholar.google.com/citations?user=X7DajBkAAAAJ
created: 2026-07-06
modified: 2026-07-06
---

# Ryan M. Bena

> [!info] Postdoctoral Scholar · Caltech AMBER Lab (Aaron D. Ames) · [scholar](https://scholar.google.com/citations?user=X7DajBkAAAAJ)

> [!note] AI-drafted bio — grounded in public sources (below); verify and refine. Homepage not located; personal-site field left blank pending confirmation.

## Bio
Postdoctoral scholar in Aaron D. Ames's **AMBER Lab** at Caltech, working on safety-critical
control — safety filters, control barrier functions, and optimization-based control for legged
robots and humanoids. PhD in Aerospace & Mechanical Engineering from **USC (2024)**, where he
worked in Néstor O. Pérez-Arancibia's Autonomous Microrobotic Systems Laboratory (AMSL) on
insect-scale robots — the SMA-driven crawling microrobot **SMARTI** and the four-wing flapping
robot **Bee++** — i.e. a background in actuation, microrobotics, and aerial-robot control before
moving into safety-critical control at Caltech. _(Training/affiliation details from ResearchGate
and USC/AMSL pages; verify before citing.)_

## Contributions to the field
- **Poisson Safety Functions (PSF)** — synthesizing a smooth, provably-valid safety function
  directly from occupancy geometry by solving a Dirichlet/Poisson PDE, giving a CBF whose zero
  level set is the obstacle boundary. Lead author of [[@bena2025geometry]].
- **Semantic / social safety filters** — extending the geometric PSF to a Laplace-modulated
  "Laplace Guidance Field" that folds semantic and social cost into the same PDE machinery
  ([[@yang2026safesage|Safe-SAGE]]).
- **CBF-constrained MPC / layered safety** for legged and humanoid platforms — safety filters
  sitting between a planner/nav command and the low-level controller.
- **Prior line (microrobotics / actuation):** SMA-actuated and flapping-wing insect-scale robots
  and their control (USC AMSL). _(Inferred focus areas from public profiles.)_

## Relevance to otto
Bena authors the **safety-filter tier** of my [[capability-aware-navigation]] stack, so his work
sits squarely on my critical path — this is why the page exists.
- **The PSF / Laplace stack is my safety filter.** In [[capability-aware-navigation]] the safety
  filter between the nav command and the low-level controller *is* the Poisson Safety Function
  ([[@bena2025geometry]], geometric) plus the semantic/social LGF ([[@yang2026safesage]]).
  See [[poisson-safety-function]] and [[control-barrier-function]]; the social side connects to
  [[social-navigation]].
- **He is a named author on the target publication.** [[@olkin2026chasing]] (Olkin, Compton,
  Bena, Ames) — we already share a byline, and his PSF line is the safety layer I'm building on.
- **Open question I'm pressing on (the payoff).** My [[capability-aware-navigation]] thread asks
  whether the PSF's *PDE structure* can yield $\nabla h$ and the Hessian more accurately/cheaply
  than finite differences. [[@bena2025geometry]] solves the Dirichlet problem via checkerboard SOR
  on a grid but appears to treat $h$ as a black-box field afterward — leaving two structural
  hooks unexploited: (1) $\mathrm{trace(Hess)}=\Delta h=f$ is *prescribed* (free consistency
  check / regularizer, and $f$ is a curvature design knob), and (2) on $\partial\Omega$, $\nabla h$
  aligns with the outward normal (direction free near the boundary). Because Poisson is linear,
  $\nabla h$ and the Hessian satisfy their own PDEs ($\Delta(\partial h/\partial x)=\partial f/\partial x$)
  and could be solved directly on the same SOR grid — most valuable in the boundary layer where FD
  is worst and the CBF constraint bites. Bena is the person to press this with. _(This is my
  inference/agenda, not a claim from his papers.)_

## In otto — authored works
_Papers already in the vault he (co-)authored:_
- **Geometric safety (PSF):** [[@bena2025geometry]] — Poisson Safety Functions (lead author).
- **Semantic / social safety:** [[@yang2026safesage]] — Safe-SAGE / Laplace Guidance Field.
- **Shared byline (humanoid running):** [[@olkin2026chasing]] — Chasing Autonomy (my own paper).

## Elsewhere (non-paper)
- [Google Scholar](https://scholar.google.com/citations?user=X7DajBkAAAAJ)
- [ResearchGate profile](https://www.researchgate.net/profile/Ryan-Bena)
- Lab: [AMBER Lab (bipedalrobotics.com)](http://www.bipedalrobotics.com/) · prior: [USC AMSL](https://sites.usc.edu/)
- Personal homepage: _not located — confirm._

## Sources
- AMBER Lab people page (bipedalrobotics.com); Google Scholar (user X7DajBkAAAAJ); ResearchGate
  (Ryan Bena — Caltech postdoc, PhD); USC AMSL / Viterbi coverage of SMARTI and Bee++ microrobots.
  Bio drafted 2026-07-06 — verify positions, dates, and homepage before citing.
