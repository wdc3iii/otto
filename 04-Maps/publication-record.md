---
type: moc
tags: [moc]
aliases: [Publications, Publication Record, CV]
created: 2026-07-06
modified: 2026-07-06
scholar: https://scholar.google.com/citations?user=Yf21RT8AAAAJ
---

# Publication Record

Canonical record of my publications, with **first-author status** made explicit. This is the
source of truth for the `website-check` skill (`.claude/scripts/website-audit` matches these
against the personal-website paper pages by arXiv id / title).

> [!note] Authorship is recorded in each paper note's frontmatter as
> `authorship: first | co-first | contributing`. For **co-first** papers I am one of several
> equal first authors — these count as first-author publications. Update the frontmatter and
> this page together.

## First-author publications
_(includes co-first — equal-contribution — authorship)_

| Paper | Venue | Year | Role | Website |
|---|---|---|---|---|
| [[@compton2024constructive\|Constructive Nonlinear Control via Zero Dynamics Policies]] | CDC | 2024 | first | ✓ `/papers/zero-dynamics-policies/` |
| [[@csomayshanklin2024robust\|Robust Agility via Learned Zero Dynamics Policies]] | IROS | 2024 | **co-first** | ✓ `/papers/agile-hopping/` |
| [[@compton2025dynamic\|Dynamic Tube MPC]] | ICRA | 2025 | first | ✓ `/papers/dynamic-tube-mpc/` |
| [[@compton2025learning\|Learning for Layered Safety-Critical Control (Predictive CBFs)]] | L4DC | 2025 | first | ✓ `/papers/predictive-control-barrier-functions/` |
| [[@terrain2026consistent\|Terrain-Consistent Reference-Guided RL for Humanoid Navigation]] | arXiv (under review) | 2026 | first | ✓ `/papers/terrain-consistent-rl/` |
| [[@compton2022deep\|Deep RL for Active Structure Stabilization]] | Data Science in Engineering | 2022 | first | ✗ (off-topic; skipped by choice) |

**First-author count: 6** (5 lead + 1 co-first). All are on the website except the 2022 paper,
which was intentionally left off (outside the current locomotion/control focus).

## Co-authored / contributing publications

| Paper | Venue | Year |
|---|---|---|
| [[@cohen2025safety\|Safety-Critical Controller Synthesis with Reduced-Order Models]] | L-CSS / ACC | 2025 |
| [[@csomayshanklin2025dynamically\|Dynamically Feasible Path Planning via Reachable Bézier Polytopes]] | ICRA | 2025 |
| [[@dai2025walk\|Walk the PLANC: Physics-Guided RL for Agile Humanoid Locomotion]] | RA-L | 2025 |
| [[@olkin2026stability\|Stability of CLF-Guided Reinforcement Learning]] | arXiv (under review) | 2026 |
| [[@olkin2026chasing\|Chasing Autonomy: Dynamic Retargeting & Control-Guided RL]] | arXiv (under review) | 2026 |
| [[@hierarchies2025motion\|Hierarchies in Motion: Layered Control to Perceptive 3D Hopping]] | T-RO (submitted) | 2025 |
| [[@contract2025theory\|A Contract Theory for Layered Control Architectures]] | TAC (submitted) | 2025 |

## Earlier / other co-authored work (not tracked in otto)
From [Google Scholar](https://scholar.google.com/citations?user=Yf21RT8AAAAJ) — pre-Caltech,
outside the vault's focus; listed for a complete record:
- K. Bhakta, J. Camargo, **W. Compton**, K. Herrin, A. Young — *Evaluation of continuous walking-speed algorithms & embedded sensors for a powered knee & ankle prosthesis* — IEEE RA-L, 2021.
- K. Bhakta, J. Maldonado-Contreras, J. Camargo, S. Zhou, **W. Compton**, et al. — *Continuous-context, user-independent, real-time intent recognition for powered lower-limb prostheses* — J. Biomechanical Engineering, 2025.

## Keeping this in sync
- Run the `website-check` skill (`.claude/scripts/website-audit`) to diff first-author papers vs. the website.
- When a paper is accepted or posted, update its note frontmatter (`authorship`, `arxiv`, `venue`) and add a row here.
- Related: [[summer-thoughts-on-autonomy]] (public lectures), [[linkedin]] (profile tracking).
