# Strict management-tier audit

Audit date: 2026-08-26; PMMC correction and second expansion: 2026-08-28

## Decision rules

- **T1:** The operative memory artifact and its access/management policy remain fixed during downstream inference. Offline formation or training, query-conditioned reads, and ordinary transient prompt/action history do not raise the tier.
- **T2:** Persistent memory content, metadata, organization, or a deliberate recurrent memory state changes during inference/deployment under a fixed update policy.
- **T3:** Feedback arising during deployment/inference persistently changes a reusable memory write, maintenance, or retrieval policy/artifact and affects later interactions or tasks. Offline SFT, RL, DPO, self-play, and pre-deployment continual learning do not qualify.

A recurrent/latent state deliberately carried across later inference steps counts as T2, including within one episode. Ordinary prompt/action history does not. Fixed per-item scoring, confidence, survival, and retention formulas are T2; only feedback-driven revision of a reusable management rule, program, adapter, or policy during deployment can be T3.

## Baseline corpus and method

The baseline audit re-reviewed all 241 architecture records present before the subsequent literature expansion against the latest primary paper version available on the audit date. The audit separately traced memory formation, deployed inference-time state changes, feedback timing, the artifact changed, persistence, and later reuse. Management leaves were checked independently; retrieval/top-k was not treated as eviction, attention was not treated as decay, and preprocessing/training was not treated as deployed updating.

Full text was available for 238 records. EMKG and SpatialGPT were adjudicated from primary publisher/proceedings material plus the official project source. VLM-MSGraph remained publisher-abstract-only; it was conservatively set to T1 and is the sole `needs_adjudication` record.

## Baseline audit results

| Metric | Before | After |
|---|---:|---:|
| T1 | 52 | 61 |
| T2 | 168 | 174 |
| T3 | 21 | 6 |
| `needs_adjudication` | 0 | 1 |
| Management leaf sets changed | — | 120 |

| Tier transition | Architectures |
|---|---:|
| T1 → T2 | 11 |
| T2 → T1 | 19 |
| T3 → T1 | 1 |
| T3 → T2 | 14 |
| Unchanged tier | 196 |

## Tier changes

| Architecture | ID | Before → after | Evidence | Rationale |
|---|---|---|---|---|
| Adaptive Workflow Agents | `adaptive-workflow-agents-2026` | T1 → T2 | PDF p. 2 | Algorithm 1 appends an LLM-generated narration to persistent workflow history during execution, so the system performs a fixed-policy T2 edit. |
| AnomalyAgent | `anomalyagent-2026` | T1 → T2 | PDF pp. 5–6 | Normal references, fixed-weight prototype updates, and reflection notes are written during operation; these are T2 state revision and editing. |
| DeepImageSearch | `deepimagesearch-2026` | T1 → T2 | PDF pp. 6, 15 | Named image subsets persist and the interaction history is replaced by a summary during use, establishing T2 update and summarization. |
| MemLearner | `memlearner-2026` | T1 → T2 | PDF p. 2 | The carried memory grows chunk by chunk during long-video inference; the update rule is fixed, so this is T2. |
| MemoryExplorer / LMEE-Bench | `memoryexplorer-lmee-bench-2026` | T1 → T2 | PDF pp. 2, 16–17 | The agent writes episodic exploration memories on the fly and reuses them across later goals; the fixed write procedure is T2. |
| MuKV | `mukv-2026` | T1 → T2 | PDF p. 5 | Streaming inference builds and prunes multimodal KV caches; carried cache state is deliberately updated and reused, so this is T2. |
| PRISM | `prism-2026` | T1 → T2 | PDF pp. 4–8 | A gated hierarchical memory carries compressed history across later visuomotor inference steps. Under the explicit recurrent-state rule this is T2, not ordinary prompt history. |
| Ptah | `ptah-2026` | T1 → T2 | PDF pp. 3–4 | The visual working memory is updated as observations arrive (M_t), so inference changes persistent operative state under fixed logic. |
| UI-KOBE | `ui-kobe-2026` | T1 → T2 | PDF p. 6 | Runtime memory records completed instructions, facts, and recent observations for later GUI steps; this is persistent inference-time editing under a fixed policy. |
| V-Mem | `v-mem-2026` | T1 → T2 | PDF p. 5 | Memory is incrementally updated at each conversation round and reused in later rounds, satisfying T2. |
| VideoLucy | `videolucy-2025` | T1 → T2 | PDF pp. 4–5 | Caption memory is iteratively rewritten and summarized across video segments during inference, satisfying T2. |
| Affordance RAG | `affordance-rag-2026` | T2 → T1 | PDF p. 3 | The image/affordance store is constructed before downstream queries and only retrieved at inference; top-k selection is not eviction. |
| AppAgent v2 | `appagent-v2-2024` | T2 → T1 | PDF p. 2 | Exploration builds operational documentation before deployment; the execution agent retrieves that fixed knowledge without persistent inference-time edits. |
| AtlasVA | `atlasva-2026` | T2 → T1 | PDF p. 3 | Atlas/exemplar-pool updates belong to PPO training. The post-training inference policy uses fixed learned artifacts, so the system is T1. |
| C-Nav | `c-nav-2025` | T2 → T1 | PDF p. 6 | Replay-buffer mutation and sampling occur during training. The deployed navigation memory/policy is fixed, so the strict inference-time tier is T1. |
| DRAE | `drae-2025` | T2 → T1 | PDF p. 2 | Memory expansion is a training/continual-learning procedure rather than a deployed inference-time update; the evaluated inference system is T1. |
| GenEvolve | `genevolve-2026` | T2 → T1 | PDF p. 3 | Privileged-teacher experience is used for training/post-training improvement; the deployed student does not update memory during inference. |
| GUI-explorer | `gui-explorer-2025` | T2 → T1 | PDF p. 3 | GUI exploration and knowledge mining precede task execution. The deployed executor reads a fixed knowledge base, so this is T1. |
| HippoMM | `hippomm-2026` | T2 → T1 | PDF p. 5 | Hierarchical memory formation precedes downstream queries; inference performs fixed retrieval over the formed artifact, not persistent cross-query editing. |
| MMA | `mma-2026` | T2 → T1 | PDF p. 2 | Query-time scoring is computed over fixed memory items and is not persisted as an update. No supported T2 operation remains. |
| Mobile-Agent-V | `mobile-agent-v-2025` | T2 → T1 | PDF p. 6 | A fixed demonstration video and its extracted guidance are consumed during execution. Sliding windows and ordinary action history do not constitute persistent memory updates. |
| Multimodal Spatial Language Maps | `multimodal-spatial-language-maps-2025` | T2 → T1 | PDF p. 2 | The map is constructed during an exploration/formation phase and then queried for downstream tasks; the paper explicitly does not center dynamic updating. Unsupported optimization, merge, and eviction leaves were removed. |
| MuSEAgent | `museagent-2026` | T2 → T1 | PDF p. 4 | The multimodal memory is built in an offline exploration/indexing phase; the paper treats online construction as future work, so deployed use is T1. |
| S3Mem | `s3mem-2026` | T2 → T1 | PDF p. 4 | The complete history is serialized and packed for a query; no persistent memory artifact is edited across downstream interactions, so this is T1. |
| SceneGraphGrounder | `scenegraphgrounder-2026` | T2 → T1 | PDF p. 3 | The scene graph is reconstructed before query answering and then read. Construction-time merge/abstraction/relinking are not inference-time T2 operations. |
| Skill-3D | `skill-3d-2026` | T2 → T1 | PDF p. 4 | The skill library co-evolves during training; deployed inference retrieves fixed skills. Offline library formation is not T2 under the strict lifecycle rule. |
| StoryAgent | `storyagent-2024` | T2 → T1 | PDF p. 2 | Subject-specific LoRA memory is trained from reference video before evaluation; deployed generation uses fixed parameters, so it is T1. |
| UI-Mem | `ui-mem-2026` | T2 → T1 | PDF p. 6 | The self-evolving memory loop runs during reinforcement-training iterations; inference retrieves the resulting fixed memory. Training-time evolution does not qualify as T2 or T3. |
| UI-Voyager | `ui-voyager-2026` | T2 → T1 | PDF p. 4 | RFT/GRSD update experience and policy during training; the deployed system does not persistently revise memory during inference, so this is T1. |
| VLM-MSGraph | `vlm-msgraph-2025` | T2 → T1 | Publisher abstract; full text unavailable | Publisher-accessible evidence supports a multi-hierarchical assembly memory, but the full paper was unavailable and does not establish an inference-time persistent update. The unsupported provisional T2 operation was removed; T1 remains conservative pending adjudication. |
| SkillGraph | `skillgraph-2026` | T3 → T1 | PDF p. 3 | Skills and graph structure evolve every K training iterations; deployed inference retrieves a fixed learned skill graph. With no inference-time memory update, this is T1. |
| AgentOCR | `agentocr-2026` | T3 → T2 | PDF p. 4 | RL trains the compression-rate controller before deployment. Inference appends and compresses the OCR buffer with fixed learned logic, yielding T2. |
| ATMem | `atmem-2026` | T3 → T2 | PDF p. 2 | STR-GRPO updates the memory mechanism during training only; inference uses the trained updater to modify state under a fixed policy, so this is T2. |
| AutoMMemo | `autommemo-2026` | T3 → T2 | PDF p. 13 | Memo-program design is optimized offline. Runtime memo state is still merged/relinked under the final fixed program, making the deployed tier T2 rather than T3. |
| CMA | `cma-2026` | T3 → T2 | PDF p. 2 | SFT/RL optimize the memory writer before deployment. Inference writes structured image episodes with a frozen policy, so this is T2. |
| Darwinian Memory | `darwinian-memory-2026` | T3 → T2 | PDF p. 4 | Runtime feedback changes fixed per-entry counters, Bayesian scores, strikes, and retention state. Because the governing formulas do not evolve, this is T2 rather than T3. |
| Mem-W | `mem-w-2026` | T3 → T2 | PDF p. 2 | The compressor/writer is trained offline and frozen at inference; only memory state is updated during use, so this is T2. |
| MemCtrl | `memctrl-2026` | T3 → T2 | PDF p. 2 | RL trains the memory controller offline. At test time the controller is frozen while recurrent memory state changes, so the highest strict tier is T2. |
| MementoGUI | `mementogui-2026` | T3 → T2 | PDF p. 4 | Training learns the gate and consolidation module. Deployment uses those frozen modules to update memory state, which is T2, not policy evolution. |
| MemOCR | `memocr-2026` | T3 → T2 | PDF p. 13 | RL/DPO train memory behavior offline. During inference a frozen model edits rich-text memory and summaries, satisfying T2 but not T3. |
| MM-Mem | `mm-mem-2026` | T3 → T2 | PDF p. 3 | The ADD/MERGE/DISCARD manager is trained offline and frozen at inference. It still changes memory content under a fixed policy, making the system T2. |
| STAMP | `stamp-gui-2026` | T3 → T2 | PDF p. 7 | Online RL is a training protocol. During deployed inference the trained model emits and carries a Memory field under a fixed policy, so this is T2. |
| VimRAG | `vimrag-2026` | T3 → T2 | PDF p. 2 | GGPO trains the compression/update behavior offline. Runtime compressed memory is generated under the frozen model, so this is T2. |
| VisMem | `vismem-2026` | T3 → T2 | PDF p. 2 | Offline RL trains the memory invocation and formation policy. Deployment uses frozen formers to update latent memory tokens, so this is T2. |
| PMMC | `pmmc-2026` | T3 → T2 | Full paper, Online Routing and Answering | Retrieval programs are compiled and verified during consolidation. Online queries only route to and execute frozen programs and cannot invoke the compiler or revise the selected program, so deployment uses a fixed policy. |

## Strict-T3 survivors

| Architecture | Qualifying target(s) | Deployment-feedback chain |
|---|---|---|
| ABot-AgentOS | `write_policy_evolution`, `retrieval_policy_evolution` | Deployment failures, user corrections, and low-confidence cases compile gated reusable evo-assets; promoted assets alter later memory writing and evidence retrieval, satisfying strict T3. (PDF pp. 12–13) |
| Evo-MedAgent | `retrieval_policy_evolution` | After each deployed/test case, outcome feedback patches persistent procedural and governance experience used to select evidence on later cases, satisfying strict T3. (PDF pp. 3–4) |
| H2-EMV | `maintenance_policy_evolution` | User feedback during ongoing deployment revises reusable relevance rules that govern later summarization and forgetting, satisfying strict T3 maintenance-policy evolution. (PDF pp. 13, 18, 21) |
| RRM | `retrieval_policy_evolution` | Test-time mini-batch feedback stores reflective retrieval procedures derived from success/failure and reuses them on later batches, satisfying strict T3. (PDF pp. 4–5) |
| TaskMem | `write_policy_evolution` | Deployment-time online learning updates a reusable adapter from recent tasks/preferences and changes later memory-writing behavior, satisfying strict T3. (PDF p. 5) |
| VisualClaw | `retrieval_policy_evolution` | Post-deployment failures create reusable skills that are injected on later queries; the persistent behavioral retrieval artifact evolves under deployed feedback, satisfying strict T3. (PDF pp. 4, 6, 19) |

## Management leaf-set changes

This table records all 120 architecture-level T2/T3 leaf-set revisions, including the 75 cases where the highest tier did not change.

| Architecture | ID | T2 before → after | T3 before → after |
|---|---|---|---|
| ABot-AgentOS | `abot-agentos-2026` | `llm_based_memory_editing`, `evidence_weighted_belief_revision` → `llm_based_memory_editing`, `evidence_weighted_belief_revision` | `maintenance_policy_evolution` → `write_policy_evolution`, `retrieval_policy_evolution` |
| Adaptive Workflow Agents | `adaptive-workflow-agents-2026` | — → `llm_based_memory_editing` | — → — |
| AesopAgent | `aesopagent-2024` | `experience_abstraction`, `optimization_based_update` → `llm_based_memory_editing`, `experience_abstraction` | — → — |
| Affordance RAG | `affordance-rag-2026` | `discrete_memory_eviction` → — | — → — |
| Agentic ASR | `agentic-asr-2026` | `evidence_weighted_belief_revision` → `llm_based_memory_editing` | — → — |
| AgentOCR | `agentocr-2026` | `episodic_or_hierarchical_summarization`, `memory_tier_migration` → `rule_based_update`, `learned_update_module` | `maintenance_policy_evolution` → — |
| AnomalyAgent | `anomalyagent-2026` | — → `evidence_weighted_belief_revision`, `llm_based_memory_editing` | — → — |
| AppAgent v2 | `appagent-v2-2024` | `rule_based_update` → — | — → — |
| AtlasVA | `atlasva-2026` | `llm_based_memory_editing`, `experience_abstraction`, `discrete_memory_eviction` → — | — → — |
| ATMem | `atmem-2026` | `learned_update_module`, `rule_based_state_correction` → `learned_update_module`, `rule_based_state_correction` | `write_policy_evolution` → — |
| AutoMMemo | `autommemo-2026` | `memory_relinking_and_reindexing`, `memory_merging_and_deduplication` → `memory_relinking_and_reindexing`, `memory_merging_and_deduplication` | `write_policy_evolution`, `maintenance_policy_evolution`, `retrieval_policy_evolution` → — |
| BrainNav | `brainnav-2026` | `optimization_based_update`, `memory_relinking_and_reindexing`, `discrete_memory_eviction` → `rule_based_update`, `memory_relinking_and_reindexing` | — → — |
| C-Nav | `c-nav-2025` | `discrete_memory_eviction` → — | — → — |
| CAUSALNAV | `causalnav-2026` | `memory_merging_and_deduplication`, `discrete_memory_eviction` → `rule_based_update`, `rule_based_state_correction`, `discrete_memory_eviction` | — → — |
| Chain-of-Memory | `chain-of-memory-gui-2025` | `llm_based_memory_editing` → `llm_based_memory_editing`, `episodic_or_hierarchical_summarization`, `discrete_memory_eviction` | — → — |
| CMA | `cma-2026` | `rule_based_update` → `rule_based_update` | `write_policy_evolution`, `retrieval_policy_evolution` → — |
| Co-Director | `co-director-2026` | `llm_based_memory_editing` → `llm_based_memory_editing`, `evidence_weighted_belief_revision` | — → — |
| Darwinian Memory | `darwinian-memory-2026` | `evidence_weighted_belief_revision`, `discrete_memory_eviction` → `evidence_weighted_belief_revision`, `discrete_memory_eviction`, `progressive_memory_decay`, `rule_based_state_correction` | `maintenance_policy_evolution` → — |
| DeepImageSearch | `deepimagesearch-2026` | — → `rule_based_update`, `episodic_or_hierarchical_summarization` | — → — |
| DGSG-Mind | `dgsg-mind-2026` | `experience_abstraction`, `memory_relinking_and_reindexing`, `discrete_memory_eviction` → `rule_based_update`, `rule_based_state_correction`, `discrete_memory_eviction`, `memory_relinking_and_reindexing` | — → — |
| DRAE | `drae-2025` | `discrete_memory_eviction` → — | — → — |
| Dream to Recall / Memoir | `dream-to-recall-memoir-2026` | `discrete_memory_eviction` → `rule_based_update` | — → — |
| Dynam3D | `dynam3d-2025` | `experience_abstraction`, `discrete_memory_eviction` → `rule_based_update`, `memory_merging_and_deduplication`, `discrete_memory_eviction` | — → — |
| ECHO | `echo-2026` | `learned_update_module`, `memory_relinking_and_reindexing`, `experience_abstraction` → `learned_update_module`, `memory_merging_and_deduplication`, `experience_abstraction`, `memory_relinking_and_reindexing` | — → — |
| Echo-MC | `echo-mc-2026` | `experience_abstraction`, `discrete_memory_eviction` → `experience_abstraction`, `rule_based_update` | — → — |
| EGAgent | `egagent-2026` | `rule_based_update`, `memory_relinking_and_reindexing` → `llm_based_memory_editing`, `episodic_or_hierarchical_summarization` | — → — |
| EgoMem | `egomem-2025` | `rule_based_update` → `llm_based_memory_editing`, `llm_based_conflict_resolution` | — → — |
| eMEM | `emem-2026` | `episodic_or_hierarchical_summarization`, `memory_tier_migration`, `memory_merging_and_deduplication` → `episodic_or_hierarchical_summarization`, `memory_tier_migration`, `memory_merging_and_deduplication`, `progressive_memory_decay` | — → — |
| EMKG | `emkg-2026` | `rule_based_update` → `rule_based_update`, `evidence_weighted_belief_revision` | — → — |
| Episodic Memory Verbalization | `episodic-memory-verbalization-2025` | `experience_abstraction`, `discrete_memory_eviction` → `episodic_or_hierarchical_summarization`, `experience_abstraction` | — → — |
| EvolvingAgent | `evolvingagent-2025` | `memory_merging_and_deduplication`, `experience_abstraction` → `optimization_based_update`, `experience_abstraction` | — → — |
| FilmAgent | `filmagent-2025` | `rule_based_update` → `llm_based_memory_editing`, `rule_based_state_correction` | — → — |
| FlexMem | `flexmem-2026` | `learned_update_module`, `memory_tier_migration` → `learned_update_module`, `memory_tier_migration`, `memory_merging_and_deduplication`, `discrete_memory_eviction` | — → — |
| GCAgent | `gcagent-2025` | `episodic_or_hierarchical_summarization`, `memory_relinking_and_reindexing` → `episodic_or_hierarchical_summarization`, `llm_based_memory_editing` | — → — |
| GEM-Occ | `gem-occ-2026` | `rule_based_state_correction`, `memory_tier_migration` → `rule_based_state_correction`, `memory_tier_migration`, `memory_merging_and_deduplication`, `discrete_memory_eviction` | — → — |
| GenEvolve | `genevolve-2026` | `experience_abstraction`, `discrete_memory_eviction` → — | — → — |
| GEST | `gest-2026` | `llm_based_memory_editing` → `rule_based_update`, `rule_based_state_correction`, `memory_relinking_and_reindexing` | — → — |
| GUI-explorer | `gui-explorer-2025` | `experience_abstraction`, `memory_relinking_and_reindexing` → — | — → — |
| HIMM | `himm-2026` | `discrete_memory_eviction` → `rule_based_update` | — → — |
| HippoMM | `hippomm-2026` | `episodic_or_hierarchical_summarization`, `experience_abstraction` → — | — → — |
| LaMem-VLA | `lamem-vla-2026` | `memory_tier_migration`, `memory_merging_and_deduplication` → `learned_update_module`, `memory_merging_and_deduplication`, `discrete_memory_eviction` | — → — |
| Light-Omni | `light-omni-2026` | `episodic_or_hierarchical_summarization`, `memory_merging_and_deduplication` → `episodic_or_hierarchical_summarization`, `memory_merging_and_deduplication`, `rule_based_update` | — → — |
| LLM-Empowered Embodied Agent for Memory-Augmented Task Planning in Household Robotics | `llm-empowered-embodied-agent-for-memory-augmented-task-planning-in-household-rob-2026` | `llm_based_memory_editing`, `progressive_memory_decay` → `rule_based_update` | — → — |
| LUMA-RAG | `luma-rag-2025` | `memory_tier_migration`, `discrete_memory_eviction` → `optimization_based_update`, `memory_tier_migration`, `rule_based_update` | — → — |
| MAGNET | `magnet-gui-2026` | `evidence_weighted_belief_revision`, `memory_relinking_and_reindexing` → `rule_based_update`, `memory_merging_and_deduplication`, `memory_relinking_and_reindexing`, `evidence_weighted_belief_revision` | — → — |
| Mem-W | `mem-w-2026` | `learned_update_module` → `learned_update_module` | `maintenance_policy_evolution` → — |
| MemCtrl | `memctrl-2026` | `learned_update_module`, `discrete_memory_eviction` → `learned_update_module` | `write_policy_evolution` → — |
| MEMENTO Personalization | `memento-personalization-2026` | `discrete_memory_eviction` → `rule_based_update`, `episodic_or_hierarchical_summarization` | — → — |
| MementoGUI | `mementogui-2026` | `learned_update_module`, `episodic_or_hierarchical_summarization`, `discrete_memory_eviction` → `learned_update_module`, `episodic_or_hierarchical_summarization` | `maintenance_policy_evolution` → — |
| MemLearner | `memlearner-2026` | — → `rule_based_update` | — → — |
| MemOCR | `memocr-2026` | `llm_based_memory_editing`, `episodic_or_hierarchical_summarization` → `llm_based_memory_editing`, `episodic_or_hierarchical_summarization` | `maintenance_policy_evolution` → — |
| Memorize-and-Generate | `memorize-and-generate-2025` | `discrete_memory_eviction` → `learned_update_module`, `memory_merging_and_deduplication`, `discrete_memory_eviction` | — → — |
| MemoryExplorer / LMEE-Bench | `memoryexplorer-lmee-bench-2026` | — → `rule_based_update` | — → — |
| MemoryVLA++ | `memoryvla-plus-plus-2026` | `memory_merging_and_deduplication` → `rule_based_update`, `memory_merging_and_deduplication` | — → — |
| MGA | `mga-2025` | `rule_based_update`, `rule_based_state_correction` → `llm_based_memory_editing`, `episodic_or_hierarchical_summarization`, `rule_based_state_correction` | — → — |
| MindForge | `mindforge-2025` | `discrete_memory_eviction` → `llm_based_memory_editing`, `experience_abstraction`, `episodic_or_hierarchical_summarization` | — → — |
| MM-Mem | `mm-mem-2026` | `episodic_or_hierarchical_summarization`, `experience_abstraction`, `memory_tier_migration` → `learned_update_module`, `episodic_or_hierarchical_summarization`, `experience_abstraction`, `memory_tier_migration`, `memory_merging_and_deduplication` | `maintenance_policy_evolution` → — |
| MMA | `mma-2026` | `evidence_weighted_belief_revision`, `progressive_memory_decay` → — | — → — |
| Mobile-Agent-V | `mobile-agent-v-2025` | `experience_abstraction`, `llm_based_memory_editing` → — | — → — |
| MobileGPT | `mobilegpt-2024` | `experience_abstraction`, `llm_based_memory_editing` → `llm_based_memory_editing`, `experience_abstraction`, `rule_based_state_correction` | — → — |
| MobileUse | `mobileuse-2025` | `experience_abstraction`, `rule_based_state_correction` → `experience_abstraction`, `rule_based_state_correction`, `rule_based_update` | — → — |
| MSGNav | `msgnav-2026` | `optimization_based_update` → `rule_based_update`, `memory_merging_and_deduplication` | — → — |
| MTU3D | `mtu3d-2025` | `optimization_based_update`, `memory_merging_and_deduplication`, `memory_tier_migration`, `discrete_memory_eviction` → `rule_based_update`, `memory_merging_and_deduplication` | — → — |
| MuKV | `mukv-2026` | — → `rule_based_update`, `memory_merging_and_deduplication`, `discrete_memory_eviction` | — → — |
| Multimodal Spatial Language Maps | `multimodal-spatial-language-maps-2025` | `optimization_based_update`, `memory_merging_and_deduplication`, `discrete_memory_eviction` → — | — → — |
| MuSEAgent | `museagent-2026` | `experience_abstraction`, `evidence_weighted_belief_revision` → — | — → — |
| ObsGraph | `obsgraph-2026` | `rule_based_update` → `rule_based_update`, `memory_merging_and_deduplication`, `memory_relinking_and_reindexing`, `discrete_memory_eviction` | — → — |
| OCR-Memory | `ocr-memory-2026` | `progressive_memory_decay` → `progressive_memory_decay`, `rule_based_update` | — → — |
| Omni-SimpleMem | `omni-simplemem-2026` | `discrete_memory_eviction` → `rule_based_update`, `memory_merging_and_deduplication`, `memory_relinking_and_reindexing` | — → — |
| One Sentence One Drama | `one-sentence-one-drama-2026` | `llm_based_memory_editing`, `evidence_weighted_belief_revision`, `discrete_memory_eviction` → `llm_based_memory_editing`, `evidence_weighted_belief_revision` | — → — |
| Open Scene Graphs | `open-scene-graphs-2024` | `experience_abstraction` → `llm_based_memory_editing`, `memory_relinking_and_reindexing` | — → — |
| Open-World 3D Scene Graph RAG | `open-world-3d-scene-graph-rag-2026` | `experience_abstraction`, `memory_relinking_and_reindexing`, `discrete_memory_eviction` → `rule_based_update`, `memory_relinking_and_reindexing` | — → — |
| Optimus-1 | `optimus-1-2024` | `experience_abstraction`, `episodic_or_hierarchical_summarization` → `experience_abstraction`, `episodic_or_hierarchical_summarization`, `discrete_memory_eviction`, `memory_merging_and_deduplication` | — → — |
| PAL-UI | `pal-ui-2025` | `episodic_or_hierarchical_summarization` → `episodic_or_hierarchical_summarization`, `rule_based_update` | — → — |
| PathNavigate | `pathnavigate-2026` | `learned_update_module`, `evidence_weighted_belief_revision` → `optimization_based_update`, `progressive_memory_decay` | — → — |
| Persode | `persode-2025` | `progressive_memory_decay` → `rule_based_update`, `experience_abstraction`, `episodic_or_hierarchical_summarization` | — → — |
| PhotoFlow | `photoflow-2026` | `experience_abstraction` → `rule_based_update`, `evidence_weighted_belief_revision` | — → — |
| Planning from Imagination | `planning-from-imagination-2025` | `memory_relinking_and_reindexing`, `discrete_memory_eviction` → `rule_based_update`, `memory_merging_and_deduplication`, `memory_relinking_and_reindexing` | — → — |
| POLAR | `polar-2026` | `rule_based_update` → `llm_based_memory_editing`, `episodic_or_hierarchical_summarization`, `experience_abstraction` | — → — |
| PRISM | `prism-2026` | — → `learned_update_module` | — → — |
| Ptah | `ptah-2026` | — → `rule_based_update` | — → — |
| Robo-Cortex | `robo-cortex-2026` | `experience_abstraction`, `discrete_memory_eviction` → `experience_abstraction`, `rule_based_update` | — → — |
| RoboEXP | `roboexp-2024` | `rule_based_update`, `rule_based_state_correction` → `rule_based_update`, `rule_based_state_correction`, `memory_relinking_and_reindexing`, `discrete_memory_eviction` | — → — |
| RoboMemory | `robomemory-2026` | `rule_based_update`, `memory_relinking_and_reindexing`, `evidence_weighted_belief_revision` → `llm_based_memory_editing`, `episodic_or_hierarchical_summarization`, `rule_based_state_correction`, `memory_relinking_and_reindexing` | — → — |
| RoboOS-NeXT | `roboos-next-2025` | `experience_abstraction`, `discrete_memory_eviction` → `rule_based_update`, `rule_based_state_correction`, `memory_relinking_and_reindexing`, `discrete_memory_eviction` | — → — |
| RRM | `rrm-2026` | `memory_merging_and_deduplication`, `progressive_memory_decay` → `llm_based_memory_editing`, `experience_abstraction` | `retrieval_policy_evolution` → `retrieval_policy_evolution` |
| S3Mem | `s3mem-2026` | `rule_based_update`, `episodic_or_hierarchical_summarization` → — | — → — |
| Scene Graph Memory | `scene-graph-memory-2023` | `memory_relinking_and_reindexing` → `rule_based_state_correction`, `memory_relinking_and_reindexing` | — → — |
| SceneGraphGrounder | `scenegraphgrounder-2026` | `memory_merging_and_deduplication`, `experience_abstraction`, `memory_relinking_and_reindexing` → — | — → — |
| SE-GA | `se-ga-2026` | `learned_update_module` → `rule_based_update`, `discrete_memory_eviction` | — → — |
| Skill-3D | `skill-3d-2026` | `memory_merging_and_deduplication`, `experience_abstraction`, `discrete_memory_eviction` → — | — → — |
| SkillGraph | `skillgraph-2026` | `experience_abstraction`, `llm_based_memory_editing` → — | `retrieval_policy_evolution` → — |
| SpatialGPT | `spatialgpt-2026` | `discrete_memory_eviction` → `rule_based_update` | — → — |
| STAMP | `stamp-gui-2026` | `learned_update_module`, `discrete_memory_eviction` → `llm_based_memory_editing` | `write_policy_evolution` → — |
| StoryAgent | `storyagent-2024` | `rule_based_update` → — | — → — |
| StoryMem | `storymem-2025` | `learned_update_module`, `discrete_memory_eviction` → `rule_based_update`, `discrete_memory_eviction` | — → — |
| StreamFlow | `streamflow-2026` | `memory_merging_and_deduplication`, `episodic_or_hierarchical_summarization` → `rule_based_update`, `memory_merging_and_deduplication`, `episodic_or_hierarchical_summarization` | — → — |
| StreamMeCo | `streammeco-2026` | `discrete_memory_eviction`, `progressive_memory_decay` → `discrete_memory_eviction` | — → — |
| StreamMind | `streammind-2026` | `episodic_or_hierarchical_summarization` → `rule_based_update`, `episodic_or_hierarchical_summarization`, `memory_relinking_and_reindexing` | — → — |
| TARIC | `taric-2026` | `rule_based_update` → `rule_based_update`, `evidence_weighted_belief_revision` | — → — |
| TaskMem | `taskmem-2026` | — → `llm_based_memory_editing` | `write_policy_evolution` → `write_policy_evolution` |
| Train the Agent Not the Expert | `train-the-agent-not-the-expert-2026` | `discrete_memory_eviction` → `memory_tier_migration`, `episodic_or_hierarchical_summarization`, `rule_based_update` | — → — |
| TRM-VLA | `trm-vla-2026` | `learned_update_module` → `learned_update_module`, `rule_based_state_correction` | — → — |
| UI-KOBE | `ui-kobe-2026` | — → `llm_based_memory_editing` | — → — |
| UI-Mem | `ui-mem-2026` | `experience_abstraction`, `memory_merging_and_deduplication`, `llm_based_conflict_resolution` → — | — → — |
| UI-Voyager | `ui-voyager-2026` | `optimization_based_update` → — | — → — |
| UniWM | `uniwm-2026` | `discrete_memory_eviction` → `rule_based_update` | — → — |
| V-Mem | `v-mem-2026` | — → `rule_based_update` | — → — |
| VideoAuteur | `videoauteur-2025` | `discrete_memory_eviction` → `rule_based_update`, `discrete_memory_eviction` | — → — |
| VideoLucy | `videolucy-2025` | — → `llm_based_memory_editing`, `episodic_or_hierarchical_summarization` | — → — |
| VIGA | `viga-2026` | `llm_based_memory_editing`, `experience_abstraction` → `rule_based_update`, `llm_based_memory_editing`, `discrete_memory_eviction` | — → — |
| ViLoMem | `vilomem-2025` | `experience_abstraction`, `llm_based_conflict_resolution` → `llm_based_memory_editing`, `memory_merging_and_deduplication`, `experience_abstraction`, `llm_based_conflict_resolution` | — → — |
| VimRAG | `vimrag-2026` | `discrete_memory_eviction` → `llm_based_memory_editing` | `maintenance_policy_evolution` → — |
| Vision to Geometry / 3DSPMR | `vision-to-geometry-3dspmr-2025` | `discrete_memory_eviction`, `progressive_memory_decay` → `rule_based_update`, `memory_relinking_and_reindexing`, `memory_merging_and_deduplication` | — → — |
| VisMem | `vismem-2026` | `learned_update_module` → `learned_update_module` | `write_policy_evolution` → — |
| VISOR | `visor-2026` | `rule_based_state_correction`, `discrete_memory_eviction` → `rule_based_update`, `episodic_or_hierarchical_summarization`, `discrete_memory_eviction` | — → — |
| VisualMem | `visualmem-2026` | `rule_based_update`, `evidence_weighted_belief_revision` → `llm_based_memory_editing`, `evidence_weighted_belief_revision`, `llm_based_conflict_resolution`, `memory_merging_and_deduplication` | — → — |
| VLM-MSGraph | `vlm-msgraph-2025` | `rule_based_update` → — | — → — |
| Where Did I Leave My Glasses? | `where-did-i-leave-my-glasses-2026` | `rule_based_update` → `rule_based_update`, `rule_based_state_correction`, `evidence_weighted_belief_revision` | — → — |

## Evidence remediation

- Replaced abstract-only/blank management pointers with full-paper or primary-source lifecycle evidence and explicit page/proceedings locations.
- Added an adjudication note to every architecture, including the exact lifecycle boundary used for its highest tier.
- Replaced unsupported eviction/decay claims where the paper only described retrieval, attention, preprocessing, candidate rejection, or training-time sampling.
- Split multi-leaf management evidence into leaf-specific paraphrases rather than sharing one generic sentence.
- Corrected Mobile-Agent-V provenance from the unrelated arXiv:2505.13887 to arXiv:2502.17110.
- Removed VLM-MSGraph's unsupported T2 operation and marked the conservative T1 record `needs_adjudication` because its full text could not be obtained; no mechanism was inferred from its name or abstract.

## Named counterexamples from the review

| Architecture | Final decision | Full-paper resolution |
|---|---:|---|
| AGMem | T1 (unchanged) | The bank is constructed from AgentNet trajectories before test-time use; inference retrieves crop-view and recovery memories but does not append the current run to the bank (PDF pp. 5–6, 13–14). |
| CogniVerse | T1 (unchanged) | Cognitive reflection is a query-time retrieval-necessity/relevance decision; the paper does not persist a reflection record for later interactions (PDF pp. 3–4). |
| MemoryExplorer | T2 (changed) | Dynamic memory update appends exploration entries during multi-goal operation and later goals reuse them (PDF pp. 2, 16–17). |
| Multimodal Spatial Language Maps | T1 (changed) | The map is formed before downstream task queries; unsupported dynamic-update, merge, and eviction leaves were removed. |
| PRISM | T2 (changed) | Its compressed history/KV state is explicitly stored and carried across later inference steps, so it follows the recurrent-state T2 rule (PDF pp. 4–8). |
| AgentCVR / Auto-scaling Continuous Memory / EvoVid | T1 (unchanged) | Their policy/encoder evolution occurs before deployment; strict T3 rejects training-time updates. |
| VisMem | T2 (changed from T3) | Offline RL learns invocation/formation; inference uses the frozen mechanism to update latent memory state. |
| UI-Voyager | T1 (changed from T2) | Its self-evolution is a training procedure and no persistent deployed memory-state update is established. |

## Complete review ledger

| Architecture | ID | Tier | Review status | Primary evidence pointer |
|---|---|---:|---|---|
| Agentic ASR | `agentic-asr-2026` | T2 | `verified` | PDF p. 3 |
| EgoMem | `egomem-2025` | T2 | `verified` | PDF p. 4 |
| MoMuSE | `momuse-2024` | T2 | `verified` | PDF p. 6 |
| PlanRAG-Audio | `planrag-audio-2026` | T1 | `verified` | PDF p. 3 |
| 3D-Mem | `3d-mem-2024` | T2 | `verified` | PDF p. 4 |
| 3DLLM-Mem | `3dllm-mem-2025` | T2 | `verified` | PDF p. 6 |
| ABot-AgentOS | `abot-agentos-2026` | T3 | `verified` | PDF pp. 12–13 |
| Affordance RAG | `affordance-rag-2026` | T1 | `verified` | PDF p. 3 |
| Analytic Concept-Centric Memory | `analytic-concept-memory-2026` | T2 | `verified` | PDF p. 4 |
| BrainNav | `brainnav-2026` | T2 | `verified` | PDF p. 4 |
| C-Nav | `c-nav-2025` | T1 | `verified` | PDF p. 6 |
| CAUSALNAV | `causalnav-2026` | T2 | `verified` | PDF p. 2 |
| CMMR-VLN | `cmmr-vln-2026` | T2 | `verified` | PDF p. 4 |
| ConceptGraphs | `conceptgraphs-2023` | T2 | `verified` | PDF p. 2 |
| DGSG-Mind | `dgsg-mind-2026` | T2 | `verified` | PDF p. 8 |
| DovSG | `dovsg-2025` | T2 | `verified` | PDF p. 2 |
| DRAE | `drae-2025` | T1 | `verified` | PDF p. 2 |
| Dream to Recall / Memoir | `dream-to-recall-memoir-2026` | T2 | `verified` | PDF p. 6 |
| Dynam3D | `dynam3d-2025` | T2 | `verified` | PDF p. 4 |
| DynaMem | `dynamem-2025` | T2 | `verified` | PDF p. 4 |
| ECHO | `echo-2026` | T2 | `verified` | PDF p. 5 |
| Echo-MC | `echo-mc-2026` | T2 | `verified` | PDF p. 4 |
| EchoVLA | `echovla-2026` | T2 | `verified` | PDF p. 7 |
| Ella | `ella-2025` | T2 | `verified` | PDF p. 5 |
| Embodied VideoAgent | `embodied-videoagent-2025` | T2 | `verified` | PDF p. 12 |
| Embodied-RAG | `embodied-rag-2024` | T2 | `verified` | PDF p. 4 |
| Embodied-SlotSSM | `embodied-slotssm-2026` | T2 | `verified` | PDF p. 6 |
| EmbodiedLGR-Agent | `embodiedlgr-2026` | T2 | `verified` | PDF p. 2 |
| eMEM | `emem-2026` | T2 | `verified` | PDF p. 3 |
| EMKG | `emkg-2026` | T2 | `verified` | Publisher pp. 4537–4544 |
| Episodic Memory Verbalization | `episodic-memory-verbalization-2025` | T2 | `verified` | PDF p. 2 |
| EvolvingAgent | `evolvingagent-2025` | T2 | `verified` | PDF p. 5 |
| GA-VLN | `ga-vln-2026` | T2 | `verified` | PDF p. 2 |
| GEM-Occ | `gem-occ-2026` | T2 | `verified` | PDF p. 2 |
| GraphEQA | `grapheqa-2025` | T2 | `verified` | PDF p. 3 |
| GraphPad | `graphpad-2025` | T2 | `verified` | PDF p. 2 |
| H2-EMV | `h2-emv-2026` | T3 | `verified` | PDF pp. 13, 18, 21 |
| HAM-VLN | `ham-vln-2026` | T2 | `verified` | PDF p. 2 |
| HIMM | `himm-2026` | T2 | `verified` | PDF p. 3 |
| KARMA | `karma-2024` | T2 | `verified` | PDF p. 3 |
| LaMem-VLA | `lamem-vla-2026` | T2 | `verified` | PDF p. 2 |
| LLM-Empowered Embodied Agent for Memory-Augmented Task Planning in Household Robotics | `llm-empowered-embodied-agent-for-memory-augmented-task-planning-in-household-rob-2026` | T2 | `verified` | PDF p. 3 |
| MAP-VLA | `map-vla-2025` | T1 | `verified` | PDF p. 4 |
| MEM | `mem-vla-2026` | T2 | `verified` | PDF p. 2 |
| MemCtrl | `memctrl-2026` | T2 | `verified` | PDF p. 2 |
| MeMento | `memento-embodied-2026` | T2 | `verified` | PDF p. 8 |
| MEMENTO Personalization | `memento-personalization-2026` | T2 | `verified` | PDF p. 3 |
| MEMORA | `memora-2026` | T2 | `verified` | PDF p. 2 |
| Memory-Augmented Object Captioning Agent | `memory-augmented-object-captioning-2026` | T2 | `verified` | PDF p. 4 |
| MemoryExplorer / LMEE-Bench | `memoryexplorer-lmee-bench-2026` | T2 | `verified` | PDF pp. 2, 16–17 |
| MemoryVLA | `memoryvla-2025` | T2 | `verified` | PDF p. 4 |
| MemoryVLA++ | `memoryvla-plus-plus-2026` | T2 | `verified` | PDF p. 4 |
| MindForge | `mindforge-2025` | T2 | `verified` | PDF p. 4 |
| MoMa-LLM | `moma-llm-2024` | T2 | `verified` | PDF p. 3 |
| MSGNav | `msgnav-2026` | T2 | `verified` | PDF p. 12 |
| MTU3D | `mtu3d-2025` | T2 | `verified` | PDF p. 2 |
| Multimodal Spatial Language Maps | `multimodal-spatial-language-maps-2025` | T1 | `verified` | PDF p. 2 |
| MUSE | `muse-3d-2026` | T2 | `verified` | PDF p. 4 |
| ObsGraph | `obsgraph-2026` | T2 | `verified` | PDF p. 3 |
| ObsMem | `obsmem-2026` | T2 | `verified` | PDF p. 7 |
| Open Scene Graphs | `open-scene-graphs-2024` | T2 | `verified` | PDF p. 2 |
| Open-World 3D Scene Graph RAG | `open-world-3d-scene-graph-rag-2026` | T2 | `verified` | PDF p. 2 |
| Optimus-1 | `optimus-1-2024` | T2 | `verified` | PDF p. 3 |
| OptimusVLA | `optimusvla-2026` | T2 | `verified` | PDF p. 2 |
| PhotoFlow | `photoflow-2026` | T2 | `verified` | PDF p. 4 |
| Planning from Imagination | `planning-from-imagination-2025` | T2 | `verified` | PDF p. 3 |
| POLAR | `polar-2026` | T2 | `verified` | PDF p. 3 |
| PRISM | `prism-2026` | T2 | `verified` | PDF pp. 4–8 |
| ReMEmbR | `remembr-2024` | T2 | `verified` | PDF p. 2 |
| RenderMem | `rendermem-2026` | T1 | `verified` | PDF p. 5 |
| Robo-Cortex | `robo-cortex-2026` | T2 | `verified` | PDF p. 4 |
| RoboEXP | `roboexp-2024` | T2 | `verified` | PDF p. 4 |
| RoboMemory | `robomemory-2026` | T2 | `verified` | PDF p. 2 |
| RoboOS-NeXT | `roboos-next-2025` | T2 | `verified` | PDF p. 3 |
| S3Mem | `s3mem-2026` | T1 | `verified` | PDF p. 4 |
| Scene Graph Memory | `scene-graph-memory-2023` | T2 | `verified` | PDF p. 3 |
| SceneGraphGrounder | `scenegraphgrounder-2026` | T1 | `verified` | PDF p. 3 |
| Skill-3D | `skill-3d-2026` | T1 | `verified` | PDF p. 4 |
| SOMA | `soma-2026` | T2 | `verified` | PDF p. 3 |
| SpatialGPT | `spatialgpt-2026` | T2 | `verified` | Proceedings pp. 423–435 |
| TARIC | `taric-2026` | T2 | `verified` | PDF p. 4 |
| TRM-VLA | `trm-vla-2026` | T2 | `verified` | PDF p. 4 |
| UniWM | `uniwm-2026` | T2 | `verified` | PDF p. 2 |
| Vision to Geometry / 3DSPMR | `vision-to-geometry-3dspmr-2025` | T2 | `verified` | PDF p. 5 |
| VLA-Pro | `vla-pro-2026` | T1 | `verified` | PDF p. 4 |
| VLM-MSGraph | `vlm-msgraph-2025` | T1 | `needs_adjudication` | Publisher abstract; full text unavailable |
| Voyager | `voyager-2023` | T2 | `verified` | PDF p. 2 |
| Where Did I Leave My Glasses? | `where-did-i-leave-my-glasses-2026` | T2 | `verified` | PDF p. 7 |
| ActionEngine | `actionengine-2026` | T2 | `verified` | PDF p. 8 |
| Adaptive Workflow Agents | `adaptive-workflow-agents-2026` | T2 | `verified` | PDF p. 2 |
| Agent S | `agent-s-2024` | T2 | `verified` | PDF p. 2 |
| AGMem | `agmem-2026` | T1 | `verified` | PDF pp. 5–6, 13–14 |
| AppAgent | `appagent-2023` | T1 | `verified` | PDF p. 2 |
| AppAgent v2 | `appagent-v2-2024` | T1 | `verified` | PDF p. 2 |
| ATMem | `atmem-2026` | T2 | `verified` | PDF p. 2 |
| Auto-scaling Continuous Memory | `auto-scaling-continuous-memory-2025` | T1 | `verified` | PDF p. 2 |
| AutoDroid | `autodroid-2024` | T1 | `verified` | PDF p. 5 |
| AutoMMemo | `autommemo-2026` | T2 | `verified` | PDF p. 13 |
| Chain-of-Memory | `chain-of-memory-gui-2025` | T2 | `verified` | PDF p. 4 |
| Darwinian Memory | `darwinian-memory-2026` | T2 | `verified` | PDF p. 4 |
| EAM | `eam-2026` | T1 | `verified` | PDF p. 3 |
| GraphPilot | `graphpilot-2026` | T1 | `verified` | PDF p. 2 |
| GUI-explorer | `gui-explorer-2025` | T1 | `verified` | PDF p. 3 |
| HyMEM | `hymem-2026` | T2 | `verified` | PDF p. 2 |
| LiteWebAgent | `litewebagent-2025` | T1 | `verified` | PDF p. 2 |
| MAGNET | `magnet-gui-2026` | T2 | `verified` | PDF p. 4 |
| Mem-W | `mem-w-2026` | T2 | `verified` | PDF p. 2 |
| MementoGUI | `mementogui-2026` | T2 | `verified` | PDF p. 4 |
| MGA | `mga-2025` | T2 | `verified` | PDF p. 10 |
| Mirage-1 | `mirage-1-2025` | T2 | `verified` | PDF p. 3 |
| MIRIX | `mirix-2025` | T2 | `verified` | PDF p. 2 |
| Mobile-Agent-V | `mobile-agent-v-2025` | T1 | `verified` | PDF p. 6 |
| Mobile-Agent-v2 | `mobile-agent-v2-2024` | T2 | `verified` | PDF p. 4 |
| MobileGPT | `mobilegpt-2024` | T2 | `verified` | PDF p. 3 |
| MobileUse | `mobileuse-2025` | T2 | `verified` | PDF p. 2 |
| OCR-Memory | `ocr-memory-2026` | T2 | `verified` | PDF p. 2 |
| PAL-UI | `pal-ui-2025` | T2 | `verified` | PDF p. 4 |
| SE-GA | `se-ga-2026` | T2 | `verified` | PDF p. 2 |
| STAMP | `stamp-gui-2026` | T2 | `verified` | PDF p. 7 |
| UI-KOBE | `ui-kobe-2026` | T2 | `verified` | PDF p. 6 |
| UI-Mem | `ui-mem-2026` | T1 | `verified` | PDF p. 6 |
| UI-Voyager | `ui-voyager-2026` | T1 | `verified` | PDF p. 4 |
| AgentOCR | `agentocr-2026` | T2 | `verified` | PDF p. 4 |
| AnomalyAgent | `anomalyagent-2026` | T2 | `verified` | PDF pp. 5–6 |
| AtlasVA | `atlasva-2026` | T1 | `verified` | PDF p. 3 |
| AUGUSTUS | `augustus-2025` | T2 | `verified` | PDF p. 20 |
| camroll-agent | `camroll-agent-2026` | T1 | `verified` | PDF p. 3 |
| CMA | `cma-2026` | T2 | `verified` | PDF p. 2 |
| CogniVerse | `cogniverse-2026` | T1 | `verified` | PDF pp. 3–4 |
| DeepImageSearch | `deepimagesearch-2026` | T2 | `verified` | PDF pp. 6, 15 |
| Evo-MedAgent | `evo-medagent-2026` | T3 | `verified` | PDF pp. 3–4 |
| GEMS | `gems-2026` | T2 | `verified` | PDF p. 2 |
| GenEvolve | `genevolve-2026` | T1 | `verified` | PDF p. 3 |
| HyLoVQA | `hylovqa-2026` | T2 | `verified` | PDF p. 2 |
| L2-VMAS | `l2-vmas-2026` | T2 | `verified` | PDF p. 6 |
| M2A | `m2a-2026` | T2 | `verified` | PDF p. 3 |
| MARDoc | `mardoc-2026` | T2 | `verified` | PDF p. 2 |
| MemEIC | `memeic-2025` | T2 | `verified` | PDF p. 7 |
| MemOCR | `memocr-2026` | T2 | `verified` | PDF p. 13 |
| MemVerse | `memverse-2025` | T2 | `verified` | PDF p. 8 |
| MMA | `mma-2026` | T1 | `verified` | PDF p. 2 |
| MuSEAgent | `museagent-2026` | T1 | `verified` | PDF p. 4 |
| NS-Mem | `ns-mem-2026` | T2 | `verified` | PDF p. 2 |
| Omni-SimpleMem | `omni-simplemem-2026` | T2 | `verified` | PDF p. 2 |
| PathNavigate | `pathnavigate-2026` | T2 | `verified` | PDF p. 4 |
| Pensieve | `pensieve-2025` | T1 | `verified` | PDF p. 4 |
| Persode | `persode-2025` | T2 | `verified` | PDF p. 3 |
| PersonaVLM | `personavlm-2026` | T2 | `verified` | PDF p. 4 |
| PixelRAG | `pixelrag-2026` | T1 | `verified` | PDF p. 9 |
| PMMC | `pmmc-2026` | T2 | `verified` | Full paper, Online Routing and Answering |
| PolarMem | `polarmem-2026` | T1 | `verified` | PDF p. 5 |
| Ptah | `ptah-2026` | T2 | `verified` | PDF pp. 3–4 |
| REVEAL | `reveal-2026` | T1 | `verified` | PDF p. 2 |
| ScrapMem | `scrapmem-2026` | T2 | `verified` | PDF p. 2 |
| SkillGraph | `skillgraph-2026` | T1 | `verified` | PDF p. 3 |
| TAME | `tame-personalization-2025` | T2 | `verified` | PDF p. 2 |
| Train the Agent Not the Expert | `train-the-agent-not-the-expert-2026` | T2 | `verified` | PDF p. 4 |
| TRAM | `tram-2026` | T2 | `verified` | PDF p. 7 |
| V-Mem | `v-mem-2026` | T2 | `verified` | PDF p. 5 |
| VIGA | `viga-2026` | T2 | `verified` | PDF p. 2 |
| ViLoMem | `vilomem-2025` | T2 | `verified` | PDF p. 3 |
| VimRAG | `vimrag-2026` | T2 | `verified` | PDF p. 2 |
| VisMem | `vismem-2026` | T2 | `verified` | PDF p. 2 |
| VISOR | `visor-2026` | T2 | `verified` | PDF p. 3 |
| VisRAG | `visrag-2024` | T1 | `verified` | PDF p. 5 |
| Visual Memory QA | `visual-memory-qa-2017` | T1 | `verified` | PDF p. 1 |
| VisualMem | `visualmem-2026` | T2 | `verified` | PDF p. 5 |
| AesopAgent | `aesopagent-2024` | T2 | `verified` | PDF p. 3 |
| AgentCVR | `agentcvr-2026` | T1 | `verified` | PDF p. 2 |
| Anim-Director | `anim-director-2024` | T1 | `verified` | PDF p. 2 |
| AniME | `anime-2025` | T2 | `verified` | PDF p. 3 |
| AViLA | `avila-2025` | T2 | `verified` | PDF p. 6 |
| CANVAS | `canvas-2026` | T2 | `verified` | PDF p. 2 |
| Co-Director | `co-director-2026` | T2 | `verified` | PDF p. 5 |
| Context-as-Memory | `context-as-memory-2025` | T2 | `verified` | PDF p. 2 |
| CuriosAI CASTLE | `curiosai-castle-2026` | T1 | `verified` | PDF p. 2 |
| Deep Video Discovery | `deep-video-discovery-2025` | T1 | `verified` | PDF p. 4 |
| DigimonGPT | `digimongpt-2026` | T2 | `verified` | PDF p. 2 |
| DreamFactory | `dreamfactory-2024` | T2 | `verified` | PDF p. 5 |
| DreamRunner | `dreamrunner-2024` | T2 | `verified` | PDF p. 4 |
| EGAgent | `egagent-2026` | T2 | `verified` | PDF p. 6 |
| EgoButler | `egobutler-2025` | T1 | `verified` | PDF p. 7 |
| EventMemAgent | `eventmemagent-2026` | T2 | `verified` | PDF p. 4 |
| EvoVid | `evovid-2026` | T1 | `verified` | PDF p. 6 |
| FilmAgent | `filmagent-2025` | T2 | `verified` | PDF p. 25 |
| Flash-VStream | `flash-vstream-2025` | T2 | `verified` | PDF p. 3 |
| FlexMem | `flexmem-2026` | T2 | `verified` | PDF p. 4 |
| FOLIO | `folio-2026` | T2 | `verified` | PDF p. 2 |
| Frames2LoRA | `frames2lora-2026` | T1 | `verified` | PDF p. 3 |
| GCAgent | `gcagent-2025` | T2 | `verified` | PDF p. 4 |
| GEST | `gest-2026` | T2 | `verified` | PDF p. 6 |
| HD-EPIC Long-Video Reasoning | `hd-epic-long-video-reasoning-2026` | T1 | `verified` | PDF p. 3 |
| HippoMM | `hippomm-2026` | T1 | `verified` | PDF p. 5 |
| Kubrick | `kubrick-2024` | T2 | `verified` | PDF p. 12 |
| Latent Spatial Memory | `latent-spatial-memory-2026` | T2 | `verified` | PDF p. 3 |
| Light-Omni | `light-omni-2026` | T2 | `verified` | PDF p. 4 |
| LongVideoAgent | `longvideoagent-2026` | T1 | `verified` | PDF p. 3 |
| LUMA-RAG | `luma-rag-2025` | T2 | `verified` | PDF p. 5 |
| M3-Agent | `m3-agent-2025` | T2 | `verified` | PDF p. 9 |
| MA-LMM | `ma-lmm-2024` | T2 | `verified` | PDF p. 2 |
| MARS | `mars-2026` | T1 | `verified` | PDF p. 3 |
| MAViS | `mavis-2025` | T2 | `verified` | PDF p. 14 |
| MemLearner | `memlearner-2026` | T2 | `verified` | PDF p. 2 |
| Memorize-and-Generate | `memorize-and-generate-2025` | T2 | `verified` | PDF p. 7 |
| MM-Mem | `mm-mem-2026` | T2 | `verified` | PDF p. 3 |
| MovieAgent | `movieagent-2025` | T1 | `verified` | PDF p. 3 |
| MovieChat | `moviechat-2023` | T2 | `verified` | PDF p. 4 |
| MovieChat+ | `moviechat-plus-2024` | T2 | `verified` | PDF p. 4 |
| MovieDreamer | `moviedreamer-2024` | T1 | `verified` | PDF p. 25 |
| MuKV | `mukv-2026` | T2 | `verified` | PDF p. 5 |
| O-MARC | `o-marc-2026` | T1 | `verified` | PDF p. 8 |
| OmAgent | `omagent-2024` | T1 | `verified` | PDF p. 3 |
| One Sentence One Drama | `one-sentence-one-drama-2026` | T2 | `verified` | PDF p. 2 |
| PyraVid | `pyravid-2026` | T2 | `verified` | PDF p. 4 |
| Reflective Dialogue VQA | `reflective-dialogue-vqa-2026` | T1 | `verified` | PDF p. 2 |
| ReflectWorld-MM | `reflectworld-mm-2026` | T2 | `verified` | PDF p. 4 |
| ReWind | `rewind-2025` | T2 | `verified` | PDF p. 2 |
| RRM | `rrm-2026` | T3 | `verified` | PDF pp. 4–5 |
| ScriptViz | `scriptviz-2026` | T1 | `verified` | PDF p. 6 |
| StoryAgent | `storyagent-2024` | T1 | `verified` | PDF p. 2 |
| StoryMem | `storymem-2025` | T2 | `verified` | PDF p. 3 |
| StreamChat | `streamchat-2025` | T2 | `verified` | PDF p. 6 |
| StreamFlow | `streamflow-2026` | T2 | `verified` | PDF p. 4 |
| StreamMeCo | `streammeco-2026` | T2 | `verified` | PDF p. 4 |
| StreamMind | `streammind-2026` | T2 | `verified` | PDF p. 5 |
| TaskMem | `taskmem-2026` | T3 | `verified` | PDF p. 5 |
| ToolMerge | `toolmerge-2026` | T1 | `verified` | PDF p. 2 |
| Vgent | `vgent-2025` | T1 | `verified` | PDF p. 5 |
| Video-EM | `video-em-2026` | T2 | `verified` | PDF p. 8 |
| VideoAgent | `videoagent-2024` | T1 | `verified` | PDF p. 6 |
| VideoARM | `videoarm-2025` | T2 | `verified` | PDF p. 2 |
| VideoAuteur | `videoauteur-2025` | T2 | `verified` | PDF p. 2 |
| VideoDirectorGPT | `videodirectorgpt-2024` | T1 | `verified` | PDF p. 4 |
| VideoGen-of-Thought | `videogen-of-thought-2024` | T2 | `verified` | PDF p. 3 |
| VideoLLaMB | `videollamb-2024` | T2 | `verified` | PDF p. 2 |
| VideoLucy | `videolucy-2025` | T2 | `verified` | PDF pp. 4–5 |
| VideoStreaming | `videostreaming-2024` | T2 | `verified` | PDF p. 3 |
| VideoStudio | `videostudio-2024` | T1 | `verified` | PDF p. 4 |
| VisualClaw | `visualclaw-2026` | T3 | `verified` | PDF pp. 4, 6, 19 |
| Vlogger | `vlogger-2024` | T1 | `verified` | PDF p. 2 |
| WorldMM | `worldmm-2026` | T2 | `verified` | PDF p. 4 |

## Reproducibility checks

The revision was validated for 241 unique architecture IDs, controlled-vocabulary leaves, tier derivation, non-empty management evidence, leaf-specific management paraphrases, and review-status consistency. Final baseline counts after the PMMC lifecycle correction are 61 T1, 174 T2, and 6 T3.

## Subsequent strict-T3 literature expansion

Expansion date: 2026-08-26

Six additional multimodal architectures were admitted after primary-source discovery and full-paper review under the same strict deployment-time T3 rule. Each addition establishes (1) feedback during deployment/inference, (2) a changed reusable policy or procedural artifact, (3) persistence, and (4) later-task use. No baseline record was relabeled in this expansion.

| Architecture | Modality | T3 target | Full-paper basis |
|---|---|---|---|
| ComfyClaw | image | retrieval policy evolution | Runtime and VLM feedback produces validated mutations to persistent skill triggers and procedures used by later workflow prompts (full paper §§3.2–3.4). |
| KnowAct-GUIClaw | GUI | retrieval policy evolution | Failed deployed skill reuse updates the same skill's retrieval description and state contracts for later subtasks (full paper §§4.2, 4.4–4.5). |
| SkeMex | image | retrieval policy evolution | The online post-deployment stream PATCHes persistent clinical-skill triggers and procedures used by subsequent tasks (full paper §§3.3–3.6; §4.2 Online Mode). |
| GeoForge | image | retrieval policy evolution | Inference-time grounded trajectories revise a safety-gated SOP and workflow candidates injected into later execution contexts (Methodology, Equations 13–18). |
| GeoEvolver | image | retrieval policy evolution | Deployed query outcomes and tool failures become persistent workflow patterns and guardrails retrieved on future queries (full paper §§3.2–3.4). |
| MobiMem | GUI | retrieval policy evolution | During deployment, user corrections evolve reusable execution templates selected for future tasks and action replay (full paper §§3, 5.1–5.3). |

| Current corpus metric | Count |
|---|---:|
| Architecture records | 247 |
| T1 | 61 |
| T2 | 174 |
| T3 | 12 |

The detailed discovery, acceptance, and exclusion rationale is recorded in `t3_deployment_expansion_report.md`.


## 2026-08-28 PMMC correction and second strict-T3 expansion

PMMC was corrected from T3 to T2 because its retrieval programs evolve during consolidation, whereas online queries only select and execute frozen compiled programs. The correction changes the original 241-record audit to 61 T1, 174 T2, and 6 T3, and the 247-record corpus after the first expansion to 61 T1, 174 T2, and 12 T3.

Five additional architectures were then admitted under the same strict four-link rule.

| Architecture | Modality | T3 target | Deployment-feedback chain |
|---|---|---|---|
| NeSy-Spatial | image | `retrieval_policy_evolution` | Post-prediction labels and verification traces revise a persistent neuro-symbolic skill library that later spatial tasks retrieve and compose. |
| SpaceMind | embodied 3D | `retrieval_policy_evolution` | Post-episode RGB/LiDAR outcomes quality-gate persistent skill mutations that later servicing episodes load. |
| Continual Harness | embodied 3D | `retrieval_policy_evolution` | Recent rendered-frame failures periodically revise persistent skills and procedures used by subsequent online steps without reset. |
| SKILL.nb | GUI | `retrieval_policy_evolution` | Runtime failures generate validated and versioned workflow repairs; later executions load the promoted procedure. |
| SymbOmni | image | `retrieval_policy_evolution` | Sequential online visual-task groups revise persistent symbolic concepts that later groups retrieve and compose. |

| Current corpus metric | Count |
|---|---:|
| Architecture records | 252 |
| T1 | 61 |
| T2 | 174 |
| T3 | 17 |

Full inclusion and exclusion rationales are recorded in `t3_deployment_expansion_report.md`.
