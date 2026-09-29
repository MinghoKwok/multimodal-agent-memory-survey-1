# Strict-T3 deployment-time literature expansion

Initial review: 2026-08-26  
Correction and second expansion: 2026-08-28  
Target branch: `taxonomy-current`

## Decision rule

This expansion uses the repository's strict T3 rule. A paper is added as T3 only when its full text supports all four links:

1. feedback is produced during deployment or inference;
2. that feedback changes a reusable memory write, maintenance, or retrieval policy artifact—not only memory contents or fixed per-item statistics;
3. the changed artifact persists beyond the current interaction; and
4. a later task or interaction uses the changed artifact.

Offline SFT, RL, DPO, self-play, a designated memory-building split followed by frozen evaluation, and ordinary runtime content accumulation are insufficient. The review used primary full-paper sources rather than titles or abstracts, and checked the method, online/deployment protocol, memory-write path, and later-use path separately.

## Added architectures

| Architecture | Modality | T3 target | Full-paper deployment chain and reason |
|---|---|---|---|
| [ComfyClaw](https://arxiv.org/abs/2607.01709) | image | `retrieval_policy_evolution` | Runtime and VLM feedback over rendered images drives validated skill mutations. REINFORCE and REVISE change persistent trigger, description, emphasis, and procedure fields used by the trigger router, and committed skill versions are invoked on later prompts (§§3.2–3.4). |
| [KnowAct-GUIClaw](https://arxiv.org/abs/2607.12625) | GUI | `retrieval_policy_evolution` | When a reused skill fails during GUI execution, the system uses the failed step, screenshot evidence, error, prior feedback, and original skill to update that skill in place. The edit can narrow its retrieval description and refresh state contracts; later GUI subtasks retrieve and validate the edited skill (§§4.2, 4.4–4.5). |
| [SkeMex](https://arxiv.org/abs/2606.09365) | image | `retrieval_policy_evolution` | The online protocol explicitly updates the repository during a stream of post-deployment clinical tasks. Outcome feedback drives CREATE/PATCH decisions; PATCH changes situational triggers and clinical procedures that persist and are retrieved by later tasks (§§3.3–3.6; §4.2 Online Mode). Utility updates alone were treated as T2, not as the reason for T3. |
| [GeoForge](https://arxiv.org/abs/2608.10494) | image | `retrieval_policy_evolution` | After inference-time Earth-observation tool execution, grounded observations and answer checks produce a safety-gated revised SOP and workflow candidates. Accepted artifacts persist in the external nonparametric state and are injected into later execution contexts to govern operation selection and composition (Methodology, Eqs. 13–18). |
| [GeoEvolver](https://arxiv.org/abs/2602.02559) | image | `retrieval_policy_evolution` | In deployed specialized workflows, judge success/validity signals and tool failures are distilled after each query into reusable tool-chain patterns and corrective guardrails. The persistent bank supplies strategy context to the orchestrator and executors on future queries (§§3.2–3.4). |
| [MobiMem](https://arxiv.org/abs/2512.15784) | GUI | `retrieval_policy_evolution` | During deployment, user interruptions and manual UI corrections are retained with the execution context. The Experience Generator compares the original plan with the correction and evolves a persistent execution template; future template selection and action replay consume the corrected procedure (§§3, 5.1–5.3). |

Each new record contains independent full-text evidence for every representation, T2 operation, and T3 target. No leaf is supported only by an abstract or architecture name.

## Corpus effect

| Metric | Before | After |
|---|---:|---:|
| Architecture records | 241 | 247 |
| T1 | 61 | 61 |
| T2 | 173 | 173 |
| T3 | 7 | 13 |

The expansion adds records only; it does not relabel any of the 241 previously audited architectures.

## Full-text candidates not added as T3

| Candidate | Decision under the strict rule |
|---|---|
| [ManimAgent](https://arxiv.org/abs/2606.30296) | The paper grows memory on a designated memory-building split and freezes snapshots for the disjoint probe evaluation. Because the reported later-use evidence is tied to this pre-probe construction protocol, deployment-time policy change is not established strongly enough for strict T3. |
| [CONTRAMEM](https://arxiv.org/abs/2608.22533) | Its memory bank is constructed from offline source trajectories and used frozen at runtime; offline construction does not qualify. |
| EmbodiSkill, XSkill, UI-Mem, AtlasVA | Their qualifying feedback/evolution occurs in training or a pre-deployment building phase, with the deployed inference artifact fixed. |
| HELPER | Deployment adds successful language-program memories under a fixed append rule; this changes contents, not the reusable management policy, so it is T2 rather than T3. |
| Dejavu, Darwinian Memory, HyMEM | Runtime trajectories, counters, graph nodes, or pruning decisions change under fixed retrieval/utility/update rules. Those are T2 state changes unless the full text shows the reusable rule or procedure itself being revised. |
| CASCADE, AdaMEM, EvolveMem, Live-Evo, Recuris | These are language/text-centric systems in their evaluated scope and therefore fall outside this multimodal taxonomy even when their online adaptation mechanism is T3-like. |

## Repository changes

- Added six architecture JSON records under `architectures/image/` and `architectures/gui/`.
- Inserted six rows into `data/architectures.csv` in modality/name order.
- Added this review report.
- Appended a dated expansion section to `tier_audit.md` so the historical 241-record audit and the current 247-record corpus are both explicit.



## 2026-08-28 correction and second expansion

### PMMC tier correction

[PMMC](https://arxiv.org/abs/2608.00962) was corrected from T3 to T2 after rechecking the paper's lifecycle boundary. PMMC compiles, executes, verifies, and stores question-conditioned retrieval programs during consolidation. At online query time, the router selects a previously compiled program and executes that frozen program; the Questioner, Planner, and Doubter are not invoked, and the query cannot replan. PMMC therefore changes persistent memory under a fixed compilation policy, but it does not show deployment-time evolution of the reusable retrieval policy.

### Additional verified strict-T3 architectures

| Architecture | Modality | T3 target | Full-paper deployment chain and reason |
|---|---|---|---|
| [NeSy-Spatial](https://arxiv.org/abs/2608.07955) | image | `retrieval_policy_evolution` | In an ordered test-then-update stream, image-based spatial predictions are recorded before labels are revealed. Post-episode labels and verification traces revise a persistent library of atomic instructions and Tool-Use/Geometry skills, and the next library state is retrieved and composed on later tasks (§§3.2–3.4; Figures 2–3). |
| [SpaceMind](https://arxiv.org/abs/2604.14399) | embodied 3D | `retrieval_policy_evolution` | After each RGB-and-LiDAR servicing episode, the complete trajectory and outcome drive create, overlay, rewrite, disable, or no-change mutations to persistent learned skill files. Quality-gated files containing triggers, rules, constraints, evidence, and provenance are loaded on later episodes (§3.5; Algorithm 1). |
| [Continual Harness](https://arxiv.org/abs/2605.09998) | embodied 3D | `retrieval_policy_evolution` | During uninterrupted rendered-frame gameplay, the Refiner periodically diagnoses recent trajectory failures and edits persistent skills, subagent procedures, strategy memory, and harness instructions in place. Subsequent online steps use the revised harness without reset (§§2.2–3.1; §4.2). |
| [SKILL.nb](https://arxiv.org/abs/2606.08049) | GUI | `retrieval_policy_evolution` | Runtime workflow failures and local repairs generate proposals that maintenance validates, refactors, versions, and promotes. Later repeated multimodal workflow executions load the promoted procedure; the qualifying T3 artifact is the revised reusable workflow, not the fixed lifecycle thresholds (§3.2; Appendix A). |
| [SymbOmni](https://arxiv.org/abs/2607.12042) | image | `retrieval_policy_evolution` | In sequential online task groups, hard and soft feedback from image/video generation and editing revises persistent concept descriptions, parameters, constraints, preconditions, and relations after each group. Later groups retrieve and compose the updated symbolic concepts (§§3.3–3.4; Appendix H). |

Each architecture meets the same four-link test: deployment-time multimodal feedback, a changed reusable memory-management artifact, persistence, and later use.

### Screened but not added

| Candidate | Decision under the strict rule |
|---|---|
| EvolveNav | Runtime outcomes append rules and update per-rule utility under fixed mechanisms; the paper does not establish evolution of the reusable management policy. |
| MemoGen | It accumulates generated memory records through a fixed union/write procedure; this is content evolution rather than policy evolution. |
| SAGEAgent | Rule learning occurs on training patients before held-out evaluation, so the evaluated deployment policy is fixed. |
| Test-Time GUI Grounding | Test-time adaptation changes the grounding model used for the current GUI task, not a persistent memory-management policy reused across later tasks. |
| SPyCE | The skill-evolution loop is part of training rather than persistent deployment-time policy evolution. |
| LOGOS and MetaForge | Both remain provisional because the available protocol evidence was insufficient to establish the complete multimodal feedback-to-persistent-policy-to-later-use chain at architecture-record confidence. |

### Current corpus effect

| Metric | After PMMC correction | After five additions |
|---|---:|---:|
| Architecture records | 247 | 252 |
| T1 | 61 | 61 |
| T2 | 174 | 174 |
| T3 | 12 | 17 |
