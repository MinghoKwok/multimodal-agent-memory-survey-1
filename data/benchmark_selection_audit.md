# Current selection: 83 resources — 17 September 2026

The broadened scope review retains all 82 existing resources and restores LoCoMo. The table no longer uses a dagger to distinguish memory-adjacent entries. Dedicated memory tests and broader tasks can both evaluate memory systems; their protocol limitations are recorded explicitly. CarMem remains a labeled text-only comparison, and WorldLines is identified as a semantic-state protocol.

See [the current scope review](benchmark_scope_review.md) and [membership manifest](table2_benchmarks.json). The records below are historical. In particular, the earlier exclusion of LoCoMo and the old dagger-derived scope flags are superseded.

---

# Table 2 benchmark selection — 2026-09-17

The selection now contains **82 resources**: the 78 previously active Table 2 rows plus MemLeak, LIBERO-Mem, MIKASA-Robo, and VideoWebArena. The existing 18 memory-adjacent markers are preserved; the count is not a claim of 82 distinct core benchmark papers. The four additions were independently checked against their primary papers. Existing retained annotations were not comprehensively re-reviewed in this update.

Inventory reconciliation: **119 − 38 + 1 = 82**. The additional inventory record is the already-listed Stateful streaming ASR evaluation protocol. Architecture records are unchanged.

Manuscript revision: [512f7a4](https://github.com/QingyueJ-nd/Multimodal-Agent-Memory-Survey/commit/512f7a46590de4e429ec759e2b6a487f3533851b).

The manifest `data/table2_benchmarks.json` is the exact membership mapping. Table panel groups are recorded separately from legacy primary-modality labels.

## Added rows and evidence

| Benchmark | Source and evidence |
|---|---|
| MemLeak | [Sections 3.1–3.3; Appendix B.4; Table 1](https://arxiv.org/html/2606.29788v1). Profiles and generated images are supplemented with real photographs. Known facts are probed after deletion and intervening turns (LE). Cross-modal leakage gives partial CE and visual-detail coverage; deletion changes retention status rather than factual world state (partial SC). The protocol does not score conflicting facts, evidence-insufficient questions, actions, entity tracking, or visual state changes. Letta is evaluated through a simulated wrapper. |
| VideoWebArena | [Sections 3.4–3.7 and 4; Appendix A.4, Table 9](https://arxiv.org/html/2410.19100v3). Recorded tutorials support constructed web tasks. Intermediate answers and final environment states are scored. Temporal-order and full-video questions support TR and ME; relevant moments are needed but timestamps are not scored (partial TL). Interface state changes indirectly exercise SC. Multimodal inputs alone do not establish complementary-evidence dependence (partial CE). Video-derived information can remain in context, so task success does not isolate memory management. |
| LIBERO-Mem | [LIBERO-Mem: non-Markovian Benchmark, pp. 3410–3411; Tables 2 and 4](https://ojs.aaai.org/index.php/AAAI/article/view/37337). Simulated manipulation tasks require object motion, sequence, relation, and occlusion histories. Object masks, instance IDs, subgoal flags, and demonstrations provide region, state, and action ground truth. History-dependent object positions and task progress support LE, SC, MA, SM, OS, and TS. Goal-conditioned visual manipulation supplies partial CE; incompatible records and unanswerable questions are not scored. |
| MIKASA-Robo (RGB+joints) | [Sections 5–6; Appendices D and K](https://arxiv.org/html/2502.10550v3). This row covers the simulated RGB+joints memory-testing configuration. State-mode oracle observations are excluded. Tasks score delayed object recall, spatial relocation, motion tracking, and ordered action sequences, supporting LE, SC, MA, SM, OS, and TS. Environment success conditions and expert trajectories supply state and action ground truth. RGB and joint inputs support partial CE; no conflict-resolution or unanswerable-query score is reported. The revised paper also evaluates VLA baselines. |

## Scope flags aligned with Table 2

- `streambench-2025`: `core_memory_benchmark` → `memory_adjacent`.
- `chronosaudio-2026`: `core_memory_benchmark` → `memory_adjacent`.
- `robograph-tsh-2026`: `core_memory_benchmark` → `memory_adjacent`.
- `dunphybench-2026`: `core_memory_benchmark` → `memory_adjacent`.
- `hiocc-2026`: `core_memory_benchmark` → `memory_adjacent`.

## Removed from the selected inventory

These records are not selected in the revised Table 2. Removal is a membership decision, not a claim that every omitted resource is invalid. Earlier records remain available in Git history.

| Record | Former path |
|---|---|
| UGC-AVQA | `benchmarks/audio_speech/ugc_avqa.json` |
| DriveSpatial | `benchmarks/embodied_3d/drivespatial.json` |
| Ego4D | `benchmarks/embodied_3d/ego4d.json` |
| IntentionNav | `benchmarks/embodied_3d/intentionnav.json` |
| PhotoFlow Missions | `benchmarks/embodied_3d/photoflow-missions.json` |
| Scene Graph Memory evaluation | `benchmarks/embodied_3d/scene-graph-memory-evaluation.json` |
| SpaceNum | `benchmarks/embodied_3d/spacenum.json` |
| AndroidWorld | `benchmarks/gui/androidworld.json` |
| Chain-of-Memory evaluation | `benchmarks/gui/chain-of-memory-evaluation.json` |
| GTA | `benchmarks/gui/gta.json` |
| GUITestScape | `benchmarks/gui/guitestscape.json` |
| Mobile-Eval-E | `benchmarks/gui/mobile-eval-e.json` |
| OSWorld | `benchmarks/gui/osworld.json` |
| PhoneWorld | `benchmarks/gui/phoneworld.json` |
| Policy-Induced Error Recovery benchmark | `benchmarks/gui/policy-induced-error-recovery-benchmark.json` |
| DDX-TRACE | `benchmarks/image/ddx-trace.json` |
| DocRetriever benchmark | `benchmarks/image/docretriever-benchmark.json` |
| FinSight Financial Report Generation Benchmark | `benchmarks/image/finsight-benchmark.json` |
| LoCoMo | `benchmarks/image/locomo.json` |
| MangaGen-MetaBench | `benchmarks/image/mangagen-metabench.json` |
| MMDR-Bench | `benchmarks/image/mmdr-bench.json` |
| REVEAL benchmark | `benchmarks/image/reveal-benchmark.json` |
| ActivityNet-QA | `benchmarks/video_streaming/activitynet-qa.json` |
| CaST-Bench | `benchmarks/video_streaming/cast-bench.json` |
| CASTLE Challenge | `benchmarks/video_streaming/castle-challenge.json` |
| CRONOS | `benchmarks/video_streaming/cronos.json` |
| Directional Motion benchmark | `benchmarks/video_streaming/directional-motion-benchmark.json` |
| DyBench | `benchmarks/video_streaming/dybench.json` |
| EgoExoMem | `benchmarks/video_streaming/egoexomem.json` |
| EgoSchema | `benchmarks/video_streaming/egoschema.json` |
| LongTVQA / LongTVQA+ | `benchmarks/video_streaming/longtvqa-longtvqa.json` |
| OMTG | `benchmarks/video_streaming/omtg.json` |
| RVS (RVS-Ego and RVS-Movie) | `benchmarks/video_streaming/rvs-streamingvqa.json` |
| Short-Drama-Bench | `benchmarks/video_streaming/short-drama-bench.json` |
| ToolMerge long-video retrieval benchmark | `benchmarks/video_streaming/toolmerge-long-video-retrieval-benchmark.json` |
| V-NIAH (Visual Needle-In-A-Haystack) | `benchmarks/video_streaming/v-niah.json` |
| VideoKR | `benchmarks/video_streaming/videokr.json` |
| VideoOdyssey | `benchmarks/video_streaming/videoodyssey.json` |
