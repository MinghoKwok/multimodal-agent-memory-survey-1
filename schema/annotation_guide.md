# Annotation guide

## Unit and scope

The quantitative unit is an **architecture/system**, not a paper. A paper can report multiple independently classifiable architectures; each receives its own `architecture_id`. Multiple papers describing the same system are linked as provenance rather than double-counted.

Include an architecture only when persistent memory is operationally important and at least one non-text modality contributes to memory formation, storage, retrieval, maintenance, policy learning, or downstream use. Exclude generic multimodal models, incidental context windows, non-memory agent papers, surveys, opinion papers, and other peripheral material.

Paper PDFs are not committed. Record the latest stable version reviewed, its persistent URL and version date.

## Primary modality

Assign exactly one folder:

- `image`
- `video_streaming`
- `gui`
- `embodied_3d`
- `audio_speech`

Use the modality that supplies the central persistent experience and primary evaluation setting. Record all other operative modalities as secondary metadata. Benchmarks use the same rule.

## Annotation order

1. Identify each persistent memory component.
2. Identify each representation path that reaches downstream computation.
3. Assign the finest representation leaf to every operative path.
4. Record storage/indexing and retrieval/activation mechanisms for every component.
5. Trace formation, inference-time state change, feedback, and later reuse as separate lifecycle events.
6. Record all persistent T2 operations.
7. Record only deployment-feedback-driven T3 policy-evolution targets.
8. Derive representation parent families, hybrid status, and highest management tier.
9. Attach leaf-specific full-paper evidence to every nontrivial assignment.

## Representation

Representation leaf labels are multi-label at architecture level and single-label per operative path:

- retained_perceptual_source_evidence
- modality_specific_encodings_and_geometric_state
- perception_to_text_records_and_summaries
- spatial_temporal_and_cross_modal_structured_memory
- persistent_multimodal_latent_state
- experience_conditioned_parametric_memory

Parent families are derived from leaves. `cross_representation_hybrid` is a derived system property, not a mutually exclusive representation family. It is true only when multiple operative representation paths are deliberately fused, routed, linked, or jointly supplied downstream. An embedding used only as an index does not create an independent latent representation path.

## Management tier: strict operational rule

Exactly one highest tier is derived:

1. A qualifying deployment/inference-time feedback-driven policy-evolution target exists → `T3`.
2. Otherwise, a qualifying persistent inference/deployment-time memory operation exists → `T2`.
3. Otherwise → `T1`.

### T1 — fixed after formation

The operative memory artifact and its access/management policy remain fixed during downstream inference. Offline formation or training, query-conditioned reads, and ordinary transient prompt/action history do not raise the tier.

Examples that remain T1 include a map, index, skill library, adapter, or demonstration memory constructed before downstream use and then only queried; top-k selection over fixed items; attention over a fixed history; and a sliding prompt window that is not retained as an operative memory artifact.

### T2 — state evolves under a fixed policy

Persistent memory content, metadata, organization, or a deliberate recurrent memory state changes during inference/deployment under a fixed update policy.

A deliberate recurrent or latent memory carried to later inference steps counts even within one episode. Ordinary prompt/action history does not count unless the architecture explicitly retains and reuses it as operative memory. Fixed formulas that revise per-item confidence, utility, survival, or retention metadata are T2; the metadata changes, but the governing policy does not.

### T3 — policy evolves from deployed feedback

Feedback arising during deployment/inference persistently changes a reusable memory write, maintenance, or retrieval policy/artifact and affects later interactions or tasks. Offline SFT, RL, DPO, self-play, and pre-deployment continual learning do not qualify.

The annotation must identify all four links: (1) feedback source during deployment/inference, (2) the reusable policy artifact changed, (3) persistence of the change, and (4) a later interaction/task affected. Training-time or offline improvement alone is never T3, even when the paper calls it online RL, self-evolution, continual learning, or feedback learning. If feedback merely changes memory content or fixed per-item statistics, assign T2.

T3 does not imply a T2 operation. Record T2 operations on T3 systems only when those operations actually occur.

## Evidence and uncertainty

Every label must cite a paper section plus a page, figure, table, algorithm, or equation when available. Evidence notes must be leaf-specific and paraphrase the mechanism, lifecycle timing, and persistent effect. Never infer a mechanism from the system name, abstract wording, or a legacy label alone. Abstract-only evidence is insufficient for a `verified` T2/T3 assignment.

Use `needs_adjudication` when full text is inaccessible or the formation/inference boundary cannot be resolved. Use `unclear` only where the controlled field permits it, and explain the unresolved point in `adjudication_notes`.
