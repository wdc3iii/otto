---
type: person
tags: [control, locomotion, rl]
aliases: [Aaron Ames, Aaron D. Ames, A. D. Ames]
created: 2026-07-06
modified: 2026-07-06
affiliation: Caltech — AMBER Lab (Mechanical & Civil Engineering / Control & Dynamical Systems)
role: Bren Professor of Mechanical & Civil Engineering and Control & Dynamical Systems
homepage: http://ames.caltech.edu/
scholar: https://scholar.google.com/citations?user=TjWwqmwAAAAJ
---

# Aaron D. Ames

> [!info] Bren Professor of Mechanical & Civil Engineering and Control & Dynamical Systems · Caltech (AMBER Lab) · [homepage](http://ames.caltech.edu/) · [scholar](https://scholar.google.com/citations?user=TjWwqmwAAAAJ)

> [!note] AI-drafted bio — grounded in public sources (below); verify and refine.

> [!important] **My PhD advisor** (William Compton), and the PI of the lab this vault's research line comes from.

## Bio
Aaron D. Ames is the **Bren Professor of Mechanical & Civil Engineering and Control & Dynamical
Systems at Caltech**, where he directs the **AMBER Lab** (A&M Bipedal Experimental Robotics, carried
over from Texas A&M). He holds a B.A. in mathematics and a B.S. in mechanical engineering from the
University of St. Thomas (2001), and an M.A. in mathematics and Ph.D. in electrical engineering &
computer sciences from **UC Berkeley (2006)**. After a postdoc in Control & Dynamical Systems at
Caltech (2006–2008), he was faculty at **Texas A&M** (from 2008) and an associate professor at
**Georgia Tech** (Woodruff School of ME + ECE) before joining Caltech in **2017**. He is an **IEEE
Fellow**; honors include the NSF CAREER award (2010), the Donald P. Eckman Award (2015), and the
IEEE CSS Antonio Ruberti Young Researcher Prize (2019). He is best known for **control barrier
functions (CBFs)**, **control Lyapunov functions (CLFs)** for locomotion, and **hybrid zero dynamics
(HZD)** — the theoretical backbone of safety-critical control and dynamic bipedal/humanoid walking.

## Contributions to the field
- **Control barrier functions (CBFs):** co-originator of the modern CBF-QP formulation for
  safety-critical control ([@ames2014barrier], [@ames2016barrier]) and author of the canonical survey
  ([@ames2019barrier]); extensions to robustness ([@xu2015robustness]), input-to-state safety,
  bounded inputs, backup sets, and composition of specifications.
- **CLFs + hybrid zero dynamics for locomotion:** **rapidly exponentially stabilizing CLFs (RES-CLFs)**
  and the CLF-QP paradigm ([@ames2014rapidly]); HZD-based 3D dynamic walking on underactuated
  humanoids ([@hereid20163d], [@ames2017hybrid]).
- **Layered / multi-rate control architectures:** reduced-order models, tube-MPC, and a nascent
  *contract theory* for hierarchical control ([@rosolia2022unified], [@matni2024theory]).
- **Safety filters and their theory:** unifying CBFs, HJ-reachability, and predictive methods
  ([@wabersich2023data]); smooth safety filters ([@cohen2023characterizing]).
- **Experimental realization:** a long line of physical bipeds/humanoids and, more recently,
  learning-based agile locomotion — theory pushed onto hardware, not just proven on paper.

## Relevance to otto
This is **the** central node of the vault: Ames is my advisor and the PI whose lab (**AMBER**)
my entire research line grows out of. The organizing thesis of otto — *inject control-theoretic
structure into learning so the result is certifiable, not merely empirically robust* — is his lab's
program, and nearly every foundational concept note here traces back to his work:
- **[[control-barrier-function]]** — his CBF-QP ([@ames2014barrier], [@ames2019barrier]) is the
  safety layer; my layered-safety work ([[@compton2025learning]]) and predictive/geometry-aware
  filters ([[@bena2025geometry]]) build directly on it.
- **[[control-lyapunov-function]]** — RES-CLFs ([@ames2014rapidly]) are the stability certificate that
  my group turns into an RL reward: **CLF-guided RL** ([[@li2026clf]], [[@olkin2026stability]],
  [[@olkin2026chasing]], [[@dai2025walk]]) is exactly "CLF structure → learned policy → certifiable
  stability."
- **[[reduced-order-model]]** / **[[dynamic-tube]]** / **[[tube-mpc]]** — ROM-based safety and
  layered planning ([@cohen2024safety], [@csomayshanklin2024bezier]) underpin my Dynamic Tube MPC
  ([[@compton2025dynamic]]).
- **[[poisson-safety-function]]** — the lab's newest safety-representation line
  ([[@bena2025geometry]], [[@yang2026safesage]]).
- **[[capability-awareness]]** — the learned-policy-limits idea sits on the same certify-what-the-
  controller-can-do instinct.

**The contrast that makes this the payoff:** Ames' classical program proves stability/safety on
*models* (HZD, CLF-QP, CBF-QP) with hardware as validation. My line — and the lab's current
direction — keeps his **certificates** but swaps model-based synthesis for **RL trained in massively
parallel simulation**, using CLF/CBF/ROM as *structure and reward* rather than as the controller
itself. Set against [[marco-hutter|Hutter]]'s scale-and-data generality, Ames anchors the opposite
pole — **structure and certification** — and my work is the attempt to fuse the two. See
[[learning-based-locomotion]] and [[rl-for-legged-locomotion]].

## In otto — authored works
_Papers already in the vault he (co-)authored (~68 notes; some are arXiv/published pairs of the same work):_

- **CBF theory & safety-critical control:** [[@ames2014barrier]] · [[@ames2016barrier]] · [[@ames2017barrier]] · [[@ames2019barrier]] (survey) · [[@xu2015robustness]] · [[@alan2023barrier]] · [[@chen2021backup]] · [[@chen2020optimal]] · [[@cohen2023characterizing]] · [[@molnar2023composing]] · [[@wang2017safe]] · [[@singletary2021comparative]]
- **Safety filters & applications:** [[@singletary2022safety]] · [[@cosner2024generative]] · [[@wabersich2023data]] · [[@chen2022interactive]]
- **Reduced-order-model safety / model-free:** [[@molnar2022model]] · [[@molnar2023safety]] · [[@cohen2024safety]] · [[@cohen2025safety]]
- **CLF & hybrid zero dynamics (bipedal walking):** [[@ames2014rapidly]] (RES-CLF) · [[@galloway2015torque]] · [[@reher2020passive]] · [[@reher2021lyapunov]] · [[@grizzle2014models]] · [[@hereid20163d]] · [[@nguyen20163d]] · [[@ames2017hybrid]] · [[@dai2022bipedal]] · [[@grey2017probabilistic]] · [[@rodriguez2022neural]] (Neural Gaits)
- **Reduced-order gait synthesis (H-LIP):** [[@xiong2022underactuated]] · [[@xiongnd3d]] · [[@xiongndglobal]]
- **Layered / multi-rate control & contract theory:** [[@csomayshanklin2022multi]] · [[@rosolia2022unified]] · [[@incer2024layered]] · [[@matni2024theory]] · [[@matni2024quantitative]] · [[@contract2025theory]] · [[@jr2024contract]] · [[@mazojr2024contract]]
- **ROM / reachable-polytope planning & tube-MPC:** [[@csomayshanklin2023nonlinear]] · [[@csomayshanklin2024bezier]] · [[@csomayshanklin2025bezier]] · [[@csomayshanklin2024dynamically]] · [[@csomayshanklin2025dynamically]] · [[@csomayshanklin2024robust]] (Robust Agility / ZDP) · [[@galliker2022planar]] · [[@hierarchies2025motion]]
- **Learning + control structure (the otto line):** [[@csomayshanklin2021episodic]] · [[@compton2024dynamic]] · [[@compton2025dynamic]] · [[@compton2024learning]] · [[@compton2025learning]] · [[@compton2024constructive]] · [[@dai2025walk]] · [[@li2025clf]] · [[@li2026clf]] · [[@olkin2025chasing]] · [[@olkin2026chasing]] · [[@olkin2026stability]]
- **Humanoid navigation / perceptive safety (newest):** [[@terrain2026consistent]] · [[@yang2026safesage]] (Poisson) · [[@bena2025geometry]] (Poisson → CBF-MPC) · [[@gu2025evolution]] (survey)

## Elsewhere (non-paper)
- Lab: [AMBER Lab](http://amberlab.weebly.com/) · Caltech [CMS profile](https://www.cms.caltech.edu/people/adames)
- Talk: ["Control Barrier Functions: Guaranteeing Safety in Theory and Practice," ADHS 2024](https://www.colorado.edu/conference/adhs2024/control-barrier-functions-guaranteeing-safety-theory-and-practice)
- Service/profiles: [IEEE CSS](https://ieeecss.org/contact/aaron-ames) · [A2C2](https://a2c2.org/contact/aaron-d-ames) · [LinkedIn](https://www.linkedin.com/in/aaron-ames) (listed as Amazon Scholar — verify)

## Sources
- Caltech homepage ([ames.caltech.edu](http://ames.caltech.edu/)) and resume; Caltech CMS profile; AMBER Lab site; Google Scholar; IEEE CSS / A2C2 bios (accessed 2026-07-06). Education, positions, and awards drawn from these; confirm before citing.
- **Uncertain / to verify:** undergraduate institution reported as **University of St. Thomas** (the task brief suggested "St. Mary's" — the web sources say St. Thomas); "Amazon Scholar" affiliation (from LinkedIn) is unverified; no founded company confirmed.
