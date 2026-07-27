# Prompt Version Comparison

## Baseline check

Confirm that versions target the same objective, input contract, runtime, and risk profile. If the task changed, report scope drift and avoid a misleading score delta.

## Compare on five axes

1. **Behavior**: expected task behavior added, removed, or changed.
2. **Contracts**: input/output schema, variables, tools, and downstream compatibility.
3. **Reliability controls**: grounding, priority, permissions, edge cases, failure and recovery.
4. **Static quality**: score every version with the same PromptOps rubric version and quote evidence.
5. **Executed results**: run the same test suite and configuration; separate pass rate, blockers, stability, and regressions.

Use `added`, `removed`, `modified`, or `unchanged` for structural changes. A score increase cannot override a new blocker or regression.

## Recommendation

- `candidate`: improvement with no blocker, regression, or incompatible change.
- `merge`: versions have complementary strengths that can be safely combined.
- `baseline`: candidate adds no material value or loses useful behavior.
- `blocked`: candidate adds a blocker, critical regression, or unresolved compatibility break.

Return the recommendation, confidence, decisive evidence, concise diff, scorecard, executed-test status, and migration notes. Explicitly label tests `not_run` when only a static comparison was possible.
