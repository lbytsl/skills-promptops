# Prompt Testing and Release Gates

## Build the test suite

Cover applicable classes:

- **Typical**: representative successful inputs.
- **Boundary**: empty, missing, oversized, malformed, multilingual, or conflicting input.
- **Adversarial**: prompt injection, authority escalation, data exfiltration, prohibited requests, or tool abuse.
- **Compliance**: authoritative-source, uncertainty, escalation, privacy, and human-review behavior.
- **Regression**: every previously fixed failure and previously passing blocking case.

For a quick suite use 5 cases: 2 typical, 1 boundary, 1 adversarial, and 1 profile-specific case. High-stakes suites require all applicable compliance cases.

## Define expected behavior

Prefer evaluation in this order:

1. deterministic assertions: schema validity, required/forbidden fields, citation IDs, tool-call constraints;
2. semantic assertions with explicit acceptable behavior and failure examples;
3. golden output only when exact wording or structure matters;
4. LLM-as-Judge only for residual qualitative criteria, with a versioned rubric and disclosed model.

Each case declares severity (`blocking` or `non_blocking`), input, expected behavior, evaluator, and rationale.

## Execute honestly

Record model identifier, full instruction stack, tool/runtime configuration, decoding parameters, dataset revision, repetitions, and raw output. If execution is unavailable, generate the suite but report `not_run`; never infer pass results.

For stability, execute each applicable case at least three times. Report schema-valid rate, semantic pass rate, blocking failure rate, and run-to-run disagreement separately.

## Verdicts

- `pass`: all assertions pass.
- `warn`: no blocking assertion fails, but a non-blocking expectation is inconsistent or uncertain.
- `fail`: any blocking assertion fails or the output violates the expected task behavior.

## Release gate

Release only when all conditions hold:

- zero blocking failures;
- zero pass-to-fail regressions;
- declared overall and profile-specific thresholds are met;
- high-stakes cases all pass and retain a human-review path;
- compatibility changes have migration notes.

Do not gate on static score alone. A high static score with unexecuted tests is at most `candidate`, never `release_ready`.
