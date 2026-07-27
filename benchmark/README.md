# PromptOps Benchmark

English · [简体中文](README.zh-CN.md)

This directory is an open collection of Prompt failure-mode fixtures, not a claim that one Prompt is universally best.

## Dataset

`dataset.jsonl` contains one JSON object per line:

- `id`: stable identifier;
- `profile`: general, rag, agent, coding, structured_output, or high_stakes;
- `risk`: low, medium, high, or critical;
- `prompt`: artifact under review;
- `expected_verdict`: blocked, needs_work, or candidate;
- `failure_labels`: expected failure taxonomy labels;
- `rationale`: human-readable adjudication basis;
- `source_type`: synthetic or anonymized_real;
- `license`: reuse terms.

## Evaluation tracks

1. **Static audit**: compare detected verdict and failure labels against fixtures.
2. **Runtime task success**: execute declared inputs and deterministic assertions.
3. **Stability**: repeat runs and report schema-valid rate, semantic pass rate, and disagreement rate.
4. **Regression**: compare a candidate version against the same baseline suite.

Never combine these tracks into an unlabeled “quality score.”

## Reproduction requirements

Publish dataset revision, model identifier, system/developer context, tool configuration, decoding parameters, number of repetitions, judge rubric/version, raw outputs, and aggregation code. Human adjudication should use at least two reviewers for disputed or high-risk cases.

The existing Markdown files are readable teaching material. Only structured fixtures with a declared protocol belong in benchmark claims.
