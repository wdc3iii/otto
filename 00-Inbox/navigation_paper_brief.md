# Capability-Aware Navigation for the Unitree G1 — Project Summary

*Goals and literature review. Compiled from project files and conversation history. Paper-stated facts are cited to their source; items inferred from framework defaults or design discussion are labeled as inferences.*

---

## 1. Project Goals and Scope

### 1.1 Overarching objective

A **general, capability-driven navigation framework** for the Unitree G1 humanoid (29 DoF, 21 actuated), with possible extension to the Themis platform. The target application is **fast autonomous campus traversal**: a single system that synthesizes walking, running, and stair-climbing and *selects speed and gait from context*, rather than tracking a fixed gait. Layered on top of the raw traversal capability are two higher-order requirements:

- **Semantic reasoning** — distinguishing traversable surfaces (sidewalks, paths) from semantically-forbidden-but-geometrically-flat regions (grass, flower beds).
- **Human-like social behavior** — appropriate interpersonal spacing and non-aggressive skirting of people, i.e. socially-compliant rather than merely collision-free motion.

### 1.2 Layered system architecture

The program is organized as a three-tier stack, and your ownership is the **middle tier**:

1. **Low-level locomotion controller (LLC)** — a *frozen* CLF-RL policy tracking SE(2) velocity commands at 50 Hz (see §2.1). This is treated as a fixed capability primitive, not retrained by the navigation layer.
2. **Mid-level navigation policy (your layer)** — a recurrent policy that consumes perception + goal state and emits SE(2) velocity commands to the LLC, sequencing the existing locomotion skills. Trained via PPO in IsaacLab using `rsl_rl`.
3. **Safety filter** — the Poisson Safety Function / Laplace Guidance Field stack (see §2.4–2.5), sitting between the navigation command and the LLC to enforce geometry-aware, semantically-modulated safety.

### 1.3 The distinguishing thesis: capability-awareness

The intended novelty is **capability-awareness**: the navigation policy should respect the *learned* LLC's emergent capability boundary, not an analytical locomotion model's assumed one. Analytical reduced-order models (LIP/H-LIP) cannot represent the true feasible-command manifold of a learned controller, so a navigation layer that plans against the analytical model will either be over-conservative or command infeasible velocities.

The concrete mechanism under investigation is the **CLF Lyapunov value $V_t = \eta^\top P \eta$** (from the LLC's own CLF-RL training) repurposed as a real-time *comfort signal*: the navigation policy is penalized for issuing commands that drive the LLC into high-$V$, out-of-distribution regimes. No prior art has been identified that uses the learned LLC's Lyapunov value as a navigation-level regularizer — this is the candidate contribution.

### 1.4 Active workstreams

- **Navigation policy architecture & training.** Recurrent mid-level policy (SRU-class or LSTM) over the frozen LLC, PPO/`rsl_rl`. Open design questions: discount factor selection (dense reward → $\gamma \approx 0.997$; see §3.1), multi-goal episode design (additive proximity + waypoint-count reward), and the capability-aware "comfort" reward built on $V_t$.
- **LiDAR encoder pretraining.** VAE-based CNN encoder for Livox Mid-360 spherical range images (70×180, 5-channel). Multi-channel reconstruction target (log-depth + surface normals + occlusion-edge mask) chosen to force the bottleneck to encode thin obstacles. Latent dim 256, $\beta = 1.0$, free bits 0.5 nats, no skip connections. Pretrained and frozen during PPO.
- **Walkable-path segmentation.** Segmenting walkable surfaces from the ZED Mini first-person camera. Current ceiling: teacher model fails on ~50% of data, limiting distillation. Ranked candidate approaches: DEVA video propagation; geometric depth teacher (surface normals + height-above-plane); foot-projection self-supervised labeling (Wild Visual Navigation pattern); VLM-prompted SAM2 propagation; multi-teacher consensus. The operational definition of "walkway" (binary mask vs. continuous traversability score) is **not yet locked**.
- **Jetson deployment pipeline.** Only the `policy_runner` node on the Jetson Orin AGX; ROS 2 topics to the minipc (best-effort QoS, depth 1, wired LAN). Policy exported as ONNX + sidecar YAML; ONNX Runtime with CUDA Execution Provider. Open decisions: custom message types vs. `Float32MultiArray`, lifecycle vs. plain node, artifact storage, action validation/fallback.
- **PSF derivative computation.** Whether the PDE structure of the Poisson Safety Function can be exploited to compute $\nabla h$ and the Hessian more accurately/efficiently than naive finite differences. Known structural facts: $\mathrm{trace}(\mathrm{Hessian}) = \Delta h = \hat f$ (forcing function gives one diagonal entry free); on $\partial\Omega$, $\nabla h$ aligns with the outward surface normal. Applicability of further exploits depends on solver representation (grid-FD/FEM vs. boundary-element), which is not yet confirmed.
- **Simulation environment.** Procedural tile generation (outdoor SMALL/MEDIUM/WALL/POLE obstacles; indoor corridor-first BSP; two-mode goal sampling mixing random geodesic goals with room-graph traversal). Real2sim pointcloud→MuJoCo pipeline explored (hybrid heightfield + CoACD convex decomposition for campus scale).

### 1.5 Target publication

**"Capability-Aware Navigation RL"** (IEEE conference; Olkin/Bena/Ames; TII support), currently early-stage. Standing critique of the draft:
- The "capability-aware" framing is not yet operationalized in the contributions.
- Contribution 1 ("first demonstration") is contestable given FocusNav (§2.8) on the G1 in Jan 2026 — should be reframed around *multi-skill / agile-gait* navigation specifically.
- Contribution 2 conflates navigation-level and locomotion-level CLF/CBF without specifying the mechanism.
- Contribution 3 states an empirical result without the principled argument (that analytical locomotion models cannot represent the learned controller's emergent capability boundary).

---

## 2. Literature Review

### In-group locomotion stack

### 2.1 CLF-RL — Control Lyapunov Function Guided Reinforcement Learning
*Li, Olkin, Yue, Ames. RA-L, accepted Dec 2025. arXiv:2508.09354.*

The foundation of the frozen LLC. CLF-RL is a **reward-shaping** framework that embeds a control Lyapunov function into the RL reward rather than enforcing it as a deployment constraint. A desired velocity $v^d$ is passed to a reference generator — either a reduced-order **H-LIP** model or a full-order **HZD** gait library — producing desired outputs $y^d_\alpha, \dot y^d_\alpha$. From the output tracking error $\eta$, a CLF $V = \eta^\top P \eta$ is constructed, where $P$ solves the CARE for the double-integrator error system $\dot\eta = A_\eta \eta + B_\eta v$ closed under the LQR gain $K_\eta = R^{-1} B_\eta^\top P$.

Two reward terms encode the CLF and its decrease condition:
- **CLF tracking:** $r_v = w_v \exp(-V_t / \sigma_v)$.
- **CLF decay:** $r_{\dot v} = -w_{\dot v}\,\mathrm{clip}\!\left((\dot V_t + \lambda V_t)/\sigma_{\dot v},\, 0, 1\right)$, penalizing insufficient decay ($\dot V_t$ approximated by finite differences $\dot V_t \approx (V_{t+1}-V_t)/\Delta t$ to avoid explicit $\dot\eta$).

Auxiliary rewards cover stance-foot holonomic constraints, torque/action-rate/joint-limit regularization. Reported reward weights: CLF tracking $w_v = 10.0$, CLF decay $w_{\dot v} = 2.0$, holonomic position $4.0$, holonomic velocity $2.0$, torque $10^{-5}$, action-rate $10^{-3}$, joint-limit $1.0$.

**Implementation:** 29-DoF G1, planning over 21 actuated DoF (hands/wrists fixed). Policy inputs: angular velocity, projected gravity, commanded linear/angular velocity, relative joint positions/velocities, previous action, and a phase encoding $\sin(2\pi t/t_\text{period}), \cos(2\pi t/t_\text{period})$ with $t_\text{period} = 0.8$ s (full gait cycle). Joint-position outputs at 50 Hz relative to a fixed symmetric standing pose. Actor and critic: MLP [512, 256, 128], ELU. HZD optimization solved offline with IPOPT + CasADi as a single-swing multiple-shooting problem.

**Key framing distinction:** Unlike potential-based shaping (which *replaces* the reward), CLF-RL *adds* a reward term designed from the structure of a valid CLF, reducing all tracking to a single Lyapunov function. The reference and CLF are used only in training → lightweight deployment. Validated on hardware with added backpack mass (HZD-CLF maintains tracking where the baseline drifts and collides) and a continuous 0.25-mile mixed-terrain outdoor walk without failures.

**Relevance to your work:** This is the primitive your navigation layer commands, and the source of the $V_t$ signal you propose to reuse as a capability/comfort penalty.

### 2.2 Chasing Stability — Humanoid Running via CLF-RL
*Olkin, Li, Compton, Ames. arXiv:2509.19573.*

Extends CLF-RL from walking to **running**, which requires handling the hybrid alternation between single-support and **flight** phases (both feet off the ground). Multi-domain trajectory optimization generates an offline gait library with SSP + flight-phase reset maps; the CLF-RL reward shaping is applied over these dynamically-feasible references. Deployed on the G1 at **~2.2 m/s**, robust to torso and foot disturbances, with accurate global reference tracking from onboard sensors only. The paper explicitly frames itself as a step toward integrating dynamic motions into a **full autonomy stack** — i.e. the layer you are building.

**Relevance:** Establishes "run" as an available skill in the multi-gait repertoire the navigation policy must learn to select, and the precedent that agile gaits are reachable through the same CLF-RL substrate.

### 2.3 Environment-Consistent Reference Synthesis via ROMs for CLF-RL over Unstructured Terrain
*Compton, Olkin, Ames. In progress.*

Synthesizes **environmentally-consistent LIP references inside the RL training loop**: footsteps are projected onto valid terrain polygons on GPU, and CoM/swing-foot height are adjusted for stairs/rough terrain. Teacher-student architecture (MLP teacher, recurrent student) conditioned on a depth camera. Draft is incomplete — reward, training, and deployment sections remain placeholder.

**Relevance:** The terrain-aware sibling of CLF-RL; directly informs the "stairs/rough terrain" leg of the multi-skill traversal goal.

### In-group safety stack

### 2.4 Geometry-Aware Predictive Safety Filters — Poisson Safety Functions to CBF-Constrained MPC
*Bena, Bahati, Werner, Cosner, Yang, Ames. arXiv:2508.11129 (Aug 2025).*

The geometric core of the safety layer. A **Poisson Safety Function (PSF)** characterizes safety by solving a Dirichlet boundary-value problem for Poisson's equation over the free-space domain $\Omega$:
$$\Delta h_0(y) = f(y)\ \ \forall y \in \Omega, \qquad h_0(y) = 0\ \ \forall y \in \partial\Omega,$$
with a smooth, strictly-negative forcing term $f$ making $h_0$ superharmonic; smoothness of $f$ yields smoothness of $h_0$, and $h_0$ is a CBF for single-integrator dynamics. The zero-superlevel set of $h_0$ implicitly defines the safe set $\mathcal{C}$ directly from perception occupancy data — no analytical obstacle primitives or SDF required.

Three extensions make it deployable on legged robots:
1. **Moving-boundary (temporal) problem.** The static Dirichlet problem is recast as a parameterized moving-boundary problem, producing a time-varying $h(\cdot, t)$ that extrapolates safe-set evolution over a finite horizon.
2. **Configuration-space lifting via Minkowski difference.** The reduced safe set $\mathcal{C}_\mathcal{Q}(q) = \mathcal{C} \ominus \mathcal{R}(q)$ (minimal pointwise reduction keeping the whole platform collision-free) is lifted into $\mathbb{R}^3 \times \mathbb{S}^3$ (or the 2D+yaw analog), giving the PSF orientation DOFs. This is what lets an asymmetric humanoid reason about *reorienting* to fit.
3. **MPC+CBF predictive filter.** Using the extended PSF as a CBF for a fully-actuated single-integrator ROM ($\dot\chi = \mu$, $\chi = [x, y, \theta]^\top$), an MPC problem with discrete-time CBF constraints over the horizon is solved by SQP; the first input $\nu_0^*$ becomes the safe velocity command to the LLC.

**Signature result:** In a narrow-corridor scenario the gap is too tight for the nominal orientation; a geometry-blind filter deadlocks, whereas this filter plans a trajectory that reorients the humanoid to align its lateral (major) axis with the corridor and passes through.

**Relevance:** Defines the safe-set representation and the PSF whose derivatives ($\nabla h$, Hessian) are the subject of your active efficiency question (§1.4).

### 2.5 Safe-SAGE — Social-Semantic Adaptive Guidance via Laplace-Modulated PSFs
*Yang, Bena, Wilkinson, Bahati, Navarro Brenes, Cosner, Ames. arXiv:2603.05497 (Mar 2026).*

Adds **semantic and social awareness** on top of the PSF stack, addressing the "semantic blindness" of geometric CBFs (a human and a chair of equal volume otherwise get identical treatment). Pipeline:

- **Semantic environment representation.** Multi-sensor point clouds fused into a robot-centric occupancy grid (hyper-elliptical self-masking, exponential decay, Gaussian smoothing). An RGB instance-segmentation network provides semantic labels; an object-level tracker associates LiDAR clusters (connected-components) with labels via greedy nearest-neighbor within a gating radius, maintaining persistent human tracks (position/velocity via exponential smoothing) even outside the camera FOV.
- **Laplace Guidance Field (LGF).** A social-semantic guidance field $v_\text{sem}$ solves a **vector Laplace** Dirichlet problem over free space, with two boundary-condition types on the orientation-parameterized domain $\Omega(\psi)$: outward-normal **repulsion** of class-dependent magnitude $b(q) < 0$ on obstacle surfaces $\partial\Omega(\psi)$, and a **tangential bias** $\lambda(q)\hat\tau$ on a buffered internal interface $\partial\Omega_r(\psi)$ (buffer via Pontryagin difference $\Omega_r = \Omega \ominus B_r$) whose sign sets passing direction (e.g. pass-on-the-right). LGFs are non-conservative (nonzero curl) — that is exactly what encodes rotational social-flow patterns.
- **Laplace-modulated PSF.** The guidance field feeds the Poisson forcing term, $\hat f \propto \nabla \cdot v_\text{sem}$, so class-aware boundary conditions propagate into $h_\text{full}$: the safety function rises faster near semantically-critical boundaries (humans) than near benign ones (walls).
- **Dual-layer filter + dynamics.** An MPC layer (linearized CBF constraints over the horizon) plus a real-time analytical CBF layer with $\sigma$-scaling for grid-artifact robustness. A motion-compensated finite-difference estimate of $\partial h_\text{full}/\partial t$ handles dynamic obstacles and perception latency.

**Reported settings & result:** $b_\text{human} = -1.7$ vs. $b_\text{objects} = -0.5$ (proposed) against a nominal $-1.0/-1.0$ baseline; the proposed modulation yields a positive human-robot margin ($0.318 \pm 0.077$ m) and larger max lateral passing offset ($0.75$ m) vs. the baseline. Platform-agnostic (reduced-order model); demonstrated on Go2 (dual LiDAR + D435) and G1.

**Relevance:** This is the "sidewalk vs. grass" and "social spacing" requirement instantiated in the safety layer — the semantic-navigation goal already has a concrete in-group realization to build against.

### External navigation lineage

### 2.6 SRU — Spatially-Enhanced Recurrent Memory for Long-Range Mapless Navigation
*Yang, Frivik, Hoeller, Wang, Cadena, Hutter. IJRR. arXiv:2506.05997.*

**The primary architectural anchor for your navigation policy.** The paper's core finding: standard RNNs (LSTM/GRU) capture temporal dependencies but are poor at **spatial memorization** — transforming and registering egocentric observations from varying perspectives into a coherent spatial representation. In a spiral-path landmark-recall task, LSTM/GRU/S4/Mamba all show high spatial error on early observations while recalling categories perfectly; the proposed **Spatially-Enhanced Recurrent Unit (SRU)** — a modification adding an implicit spatial-transformation operation to LSTM/GRU — keeps spatial error low across all steps.

**Architecture:** pretrained depth encoder → self-attention (spatial context enrichment) → cross-attention (query from proprioceptive state $o^\text{prop}_t$ = linear/angular velocity, projected gravity, previous action, plus relative goal $p_t$; compresses the $C\times H\times W$ feature map to $C\times 1$) → SRU (fuses compressed feature with $o^\text{prop}_t$, $p_t$, and $h_{t-1}$; the proprioceptive state supplies the ego-motion equivalent to the frame transform) → MLP head emitting velocity commands to the locomotion controller. End-to-end RL, single forward-facing stereo camera.

**Depth-encoder pretraining (critical for you):** a RegNet backbone + FPN, pretrained for **VAE self-reconstruction on large-scale synthetic depth (TartanAir)** with a **parallelizable depth-noise model**. The stated motivation is **sim-to-real robustness** — latent-space analysis shows the large-scale-pretrained encoder's feature distribution covers real-world data, while an encoder trained only on RL-collected sim images does not (higher Mahalanobis distance to real features). This is the precedent for your Livox VAE encoder plan, and the reason pretraining is framed as robustness-first, not compute-first.

**Regularization:** temporally-consistent dropout (same mask across rollout timesteps) + deep mutual learning are reported as crucial to prevent early convergence in end-to-end recurrent RL.

**Reported gains:** +23.5% over other RNNs; +29.6% vs. explicit-mapping baseline; +105.0% vs. stacked-observation baseline; zero-shot sim-to-real across indoor/outdoor/forest.

### 2.7 Wheeled-Legged Kilometer-Scale Navigation
*Lee et al. Science Robotics 2024. arXiv:2405.01792.*

**The most completely-specified training setup in the Hutter lineage**, and your published precedent for the HLC/LLC discount-factor split. Two-level HRL on a wheeled-legged ANYmal: a **navigation policy (HLC) at 10 Hz** issues velocity targets to a **locomotion policy (LLC) at 50 Hz**. The HLC consumes the **LLC's belief/hidden state** (capturing terrain properties and disturbances), a local height map with safety margin, and **20 previously-visited positions at 50 cm intervals** (~10 m of history). Explicitly-defined sub-goals (velocity commands) were chosen over learned latent sub-goals for modular development and LLC reuse. Training uses procedural **Wave-Function-Collapse** environments with a "navigation graph" defining feasible paths, rewarding shortest-path following. Kilometer-scale autonomous deployments in Zurich and Seville.

**Relevance:** Direct template for the two-tier HLC-over-frozen-LLC design, the belief-state-as-HLC-input pattern, and the precedent that HLC $\gamma$ can differ from (and exceed) LLC $\gamma$ (§3.1).

### 2.8 FocusNav — Spatial Selective Attention with Waypoint Guidance
*Zhang, Ma, Yan, Cao, Zhang, Li, Gao (SJTU / Shanghai Innovation Institute). arXiv:2601.12790 (Jan 2026).*

**The direct contemporary competitor on the exact platform.** A humanoid *local* navigation framework on the Unitree G1, motivated by a biological "Perception-Prediction-Attention" paradigm. Two mechanisms:
- **Waypoint-Guided Spatial Cross-Attention (WGSCA):** anchors environmental feature aggregation to a sequence of predicted collision-free waypoints, so perception is spatially aligned with intended trajectory.
- **Stability-Aware Selective Gating (SASG):** truncates distal environmental information when the robot's stability decreases, forcing the policy to prioritize immediate foothold safety.

A GRU-based control policy consumes a selectively-gated hybrid-map embedding + robot state. Trained by **behavior cloning** from a privileged **GuideOracle** (a PPO oracle with full simulator observability for waypoint tracking) in IsaacGym across 4× RTX 4090, over rugged terrain (stairs, slopes, gaps) with static forest-like pillars and dynamic obstacles. Hardware: G1 with Livox MID-360 + RealSense D435i; Fast-LIO for relative localization.

**Relevance / threat:** FocusNav establishes prior "humanoid navigation on G1" work as of Jan 2026, so a bare "first humanoid navigation demonstration" claim is dead on arrival. Note the wedge, though: FocusNav is *local* navigation with a velocity-command LLC and does **not** address multi-skill agile-gait selection (walk/run/stairs) or a learned capability boundary — which is precisely where your reframed Contribution 1 should live. FocusNav's SASG (stability-based perceptual gating) is conceptually adjacent to your $V_t$-comfort idea and should be distinguished explicitly: SASG gates *perception* on a stability heuristic; your proposal penalizes *commands* on the LLC's own certified Lyapunov value.

### 2.9 Additional lineage references

- **Hoeller et al. 2021** (RA-L; arXiv:2103.04351) — VAE+LSTM navigation predecessor; the earlier point in the same ETH line that SRU supersedes.
- **Roth et al. — FDM + MPPI** (arXiv:2504.19322) — forward dynamics model with sampling-based MPPI planning; relevant as an alternative mid-level formulation.
- **Haro et al. — Path-Conditioned RL** (arXiv:2603.13888; ETH RSL) — conditioning locomotion RL on a path; relevant to the path-segmentation → navigation interface.

### Method / architecture references

- **DD-PPO** (arXiv:1911.00357) — the most complete published recurrent-PPO configuration in embodied AI; reference for your `rsl_rl` recurrent PPO setup.
- **PointPainting** (arXiv:1911.10150) — camera→LiDAR semantic fusion by decorating points with segmentation scores; relevant to fusing ZED-Mini walkable-path segmentation into the LiDAR representation.
- **Topological navigation (Berkeley / Levine): GNM, ViNT, NoMaD** — the longer-horizon direction (sparse semantic/topological maps over dense SLAM). Combined with OSM as a campus prior, and the candidate novelty of **capability-annotated edges** (walkable / runnable / stairs) not addressed by wheeled-robot topo-nav or indoor scene-graph work.

---

## 3. Cross-Cutting Principles and Positioning

### 3.1 Discount factor is coupled to reward density
Sparse/terminal rewards need *higher* $\gamma$ to propagate the terminal signal to early states (at $\gamma = 0.99$ over 600 steps, a terminal reward is attenuated ~400× at early states). The Hutter lineage keeps effective credit-propagation distance short via rolling waypoints and dense bootstrapping curricula, permitting $\gamma \approx 0.99$–$0.991$; Lee et al. (§2.7) publishes HLC $\gamma = 0.991 >$ LLC $\gamma = 0.99$. Your dense reward with a rarely-firing terminal convergence reward warrants $\gamma \approx 0.997$.

### 3.2 VAE bottleneck encodes thin features only if the loss targets them
In a true bottleneck VAE with no skip connections, the decoder has no access to the input, so what the encoder compresses is shaped entirely by the reconstruction loss. Depth-only reconstruction will drop thin obstacles (railings, poles); heavily-weighted sparse edge/normal channels force their encoding. This is why the Livox target is 5-channel (log-depth + normals + occlusion-edge mask), not depth alone.

### 3.3 MuJoCo convex-hull collision is a real2sim trap
MuJoCo mesh collision defaults to the convex hull; thin structures are silently destroyed by decimation/hull approximation, creating a mismatch between perception training targets (which *do* see thin obstacles, per §3.2) and collision geometry. Escape routes: heightfields for navigable terrain, CoACD convex decomposition for discrete obstacles.

### 3.4 Where the review is currently thin (reviewer-facing gaps)
- **No cited prior art for capability-awareness.** The $V_t$-as-navigation-regularizer idea needs a positioned *negative* result ("no prior work uses the learned LLC's Lyapunov value as a navigation-level comfort penalty") to stand as a contribution rather than an assertion.
- **The FocusNav overlap** means the "first" claim must be narrowed to multi-skill / agile-gait navigation with an explicit SASG-vs-$V_t$ distinction (§2.8).
- **CLF/CBF layer conflation** (draft Contribution 2) — the review cleanly separates the *locomotion-level* CLF (§2.1, training-time reward) from the *navigation/safety-level* CBF (§2.4–2.5, deployment-time filter); the paper must state which mechanism the navigation policy actually wires in, and at which layer.
- **Scope boundary** — whether a high-level semantic/topological planner (§2.9) is in scope for this paper or a separate contribution is unresolved.

---

## 4. Citation Index

| Ref | Work | Venue / ID | Role in project |
|---|---|---|---|
| §2.1 | CLF-RL (Li, Olkin, Yue, Ames) | RA-L 2025; arXiv:2508.09354 | Frozen LLC; source of $V_t$ |
| §2.2 | Chasing Stability (Olkin, Li, Compton, Ames) | arXiv:2509.19573 | Running skill |
| §2.3 | Environment-Consistent Reference Synthesis (Compton, Olkin, Ames) | in progress | Terrain-aware LLC sibling |
| §2.4 | Geometry-Aware Predictive Safety Filters (Bena et al.) | arXiv:2508.11129 | PSF/LGF geometric core |
| §2.5 | Safe-SAGE (Yang, Bena, et al.) | arXiv:2603.05497 | Semantic/social safety layer |
| §2.6 | SRU (Yang, Frivik, Hoeller, Wang, Cadena, Hutter) | IJRR; arXiv:2506.05997 | Nav-policy architecture anchor |
| §2.7 | Wheeled-legged nav (Lee et al.) | Science Robotics 2024; arXiv:2405.01792 | HLC/LLC HRL template |
| §2.8 | FocusNav (Zhang et al.) | arXiv:2601.12790 | Direct G1 competitor |
| §2.9 | Hoeller et al. 2021 | RA-L; arXiv:2103.04351 | VAE+LSTM predecessor |
| §2.9 | Roth et al. (FDM+MPPI) | arXiv:2504.19322 | Alt. mid-level formulation |
| §2.9 | Haro et al. (Path-Conditioned RL) | arXiv:2603.13888 | Path→nav interface |
| §2.9 | DD-PPO | arXiv:1911.00357 | Recurrent-PPO config ref |
| §2.9 | PointPainting | arXiv:1911.10150 | Camera-LiDAR fusion |
| §2.9 | GNM / ViNT / NoMaD | Berkeley/Levine | Topological-nav direction |

*Note: a reference given in the request as arXiv:2606.10832 could not be located in the project files or conversation history and is not verifiable; it has been omitted rather than fabricated. Provide the title/authors to include it.*
