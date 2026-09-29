# Derived data

These CSV files are generated indexes for audit and analysis. Canonical annotations live in the JSON records under `architectures/` and `benchmarks/`. Derived taxonomy fields must follow `schema/counting_rules.md`.

## Benchmark selection

The benchmark inventory matches the **83 resources selected in manuscript Table 2**. It includes dedicated memory tests, broader task and component evaluations, and explicitly scoped comparisons; the total is not a count of distinct dedicated multimodal-memory benchmark papers. LoCoMo is included with its caption-based QA qualification. CarMem is text-only, and WorldLines uses semantic household traces.

See [the membership manifest](table2_benchmarks.json), [the complete scope review](benchmark_scope_review.md), and [the historical selection audit](benchmark_selection_audit.md). Legacy `scope_status` values are descriptive metadata, not exclusion rules. The scope review states the evidence level and limitations for each resource.
