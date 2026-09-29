# Counting rules for cross-axis analysis

- Count architectures, not papers.
- Count each architecture once in the highest-tier distribution.
- Representation-family and mechanism analyses use architecture-level binary incidence: a label contributes at most one count per architecture even if several components share it.
- Representation-path analyses are separate and must be explicitly named as path-level.
- A benchmark is never counted as an architecture unless the paper also introduces a distinct memory architecture; in that case create separate benchmark and architecture records linked to the same paper.
- Parent representation families, hybrid status, T2 parent operations, source recoverability, and highest tier are derived fields.
- `usable_source_route = true` when at least one operative path is `direct` or `linked_recoverable`.
- Missing and `unclear` values remain explicit denominators; do not silently drop them.
- Report counts and percentages with denominators, and retain the record IDs used for every figure or table.
- For architecture publication-year figures, use the four-digit year suffix of `architecture_id`; `latest_version.published_date` is the date of the reviewed version and must not be used as the original publication year.
