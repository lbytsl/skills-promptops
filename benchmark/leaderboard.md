# Prompt Score Leaderboard

English · [简体中文](leaderboard.zh-CN.md)

> Archived teaching artifact. Scores below use the legacy rubric and are not reproducible cross-model benchmark results. New claims must follow [README.md](README.md).

## Archived batch result

Evaluation date: 2026-07-27  
Legacy mode: batch evaluation  
Artifacts: 11 (five positive examples and six failed examples)

### Summary

| Metric | Archived value |
|---|---:|
| Overall average | 66 |
| Positive-example average | 90 |
| Failed-example average | 42 |
| Historical S share | 45% |
| Historical A-or-higher share | 64% |
| Historical D share | 55% |
| Legacy red-line caps | 5 |

### Ranking

| Rank | Prompt ID | Scenario | Historical score | Grade | Main deduction |
|---:|---|---|---:|---|---|
| 1 | customer-service | E-commerce support | 92 | S | — |
| 2 | construction-cost | Construction cost review | 91 | S | Missing pricing-boundary example |
| 3 | rag-agent | RAG retrieval | 90 | S | Missing conflicting-source example |
| 4 | legal-contract | Contract review | 89 | A | Example covers only two of five dimensions |
| 5 | coding-agent | Code review | 88 | A | Single-language example |
| 6 | bad-case-2 | Medical-record review | 52 | D | Missing anti-fabrication control; overloaded task |
| 7 | bad-case-3 | Legal advice | 48 | D | Missing sources and grounding |
| 8 | bad-case-6 | Cost review with scope drift | 46 | D | Unsupported pricing and prediction tasks |
| 9 | bad-case-4 | Weekly report | 42 | D | Conflicting instructions |
| 10 | bad-case-5 | Unguarded RAG assistant | 38 | D | Injection and fabrication exposure |
| 11 | bad-case-1 | Vague customer support | 24 | D | Core contracts absent |

### Archived loss distribution

| Legacy dimension | Common failure |
|---|---|
| Task instruction | Task overload, vague scope, unsafe synthesis |
| Boundaries | No anti-fabrication or prohibited-action rules |
| Output format | No field-level contract |
| Success criteria | Subjective quality adjectives |
| Examples | No calibration examples |
| Role | Broad labels without useful authority boundaries |
| Context and evidence | Missing standards or source documents |
| Input | Undefined input boundary |

The old numbers are retained for historical transparency only. Do not use them as a release gate. Current releases must report blockers, executed tests, runtime configuration, and regression status separately.
