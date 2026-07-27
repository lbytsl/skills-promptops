# PromptOps Structured Contract

This optional contract supports Agent routers and workflow integrations. Human conversation does not need JSON.

## Request

```json
{
  "schema_version": "0.2",
  "operation": "design | evaluate | improve | compare | test",
  "language": "auto",
  "profile": "auto | general | rag | agent | coding | structured_output | high_stakes",
  "artifact": {
    "prompt": "string",
    "candidate_prompt": "string or null",
    "requirements": "string or object or null"
  },
  "runtime": {
    "model": "string or unknown",
    "tools": [],
    "output_consumer": "human | machine | both | unknown"
  },
  "options": {
    "include_revision": true,
    "include_tests": true,
    "execute_tests": false
  }
}
```

Required fields are `schema_version`, `operation`, and the artifact appropriate to the operation. Never claim execution when `execute_tests` is false or no runtime is available.

## Response

```json
{
  "schema_version": "0.2",
  "operation": "evaluate",
  "profile": "rag",
  "verdict": "blocked | needs_work | candidate | release_ready",
  "static_score": 41,
  "confidence": "high",
  "execution_status": "not_run | partial | complete",
  "blocking_risks": [
    {"label": "missing_evidence_boundary", "evidence": "quoted text", "impact": "string"}
  ],
  "scorecard": [
    {"dimension": "grounding", "score": 2, "max": 15, "evidence": "string", "gap": "string"}
  ],
  "recommendations": [
    {"priority": "P0", "change": "string", "reason": "string"}
  ],
  "revised_prompt": "string or null",
  "comparison": null,
  "tests": [],
  "release_gate": {"status": "not_run", "blocking_failures": []}
}
```

For `compare`, populate `comparison` with structural/capability changes, score deltas, regressions, recommendation, and migration notes. For `test`, populate each test with ID, class, severity, input, expected behavior, evaluator, and—only after execution—actual output and verdict.

## Compatibility

Consumers must ignore unknown response fields. New optional fields are minor-version compatible; removing fields or changing enum semantics requires a major version. Preserve `schema_version` in stored results.
