# High-scoring Prompt Examples

English · [简体中文](good-prompts.zh-CN.md)

> Legacy teaching examples. Historical scores use the original eight-element rubric and do not demonstrate runtime reliability. Re-evaluate with the current rubric before release.

## 1. E-commerce customer support — historical score 92

See `examples/customer-service.md`.

- Uses a verify → conclude → guide sequence instead of vague prohibitions.
- Separates permission, fabrication, and escalation boundaries.
- Expresses acceptance criteria as mechanically checkable conditions.

## 2. RAG knowledge-base agent — historical score 90

See `examples/rag-agent.md`.

- Uses variable inputs that can map to a retrieval workflow.
- Prevents unsupported model-knowledge framing.
- Defines a separate path when retrieval cannot support an answer.
- Exposes a confidence signal that downstream workflows can route.

## 3. Code review agent — historical score 88

See `examples/coding-agent.md`.

- Parameterizes the programming language.
- Defines Critical, Major, and Minor severity levels.
- Marks uncertain security findings for confirmation instead of forcing a conclusion.

## 4. Construction cost review — historical score 91

See `examples/construction-cost.md`.

- Adds anti-fabrication, pricing-boundary, and human-review controls for a high-stakes task.
- Converts subjective severity into a measurable financial threshold.
- Separates confirmed findings from items requiring review.
- Prevents scope drift into bidding strategy.

## 5. Contract risk review — historical score 89

See `examples/legal-contract.md`.

- Parameterizes the represented party because the review perspective changes the result.
- Requires directly usable replacement language rather than generic advice.
- Separately reports one-sided obligations.
- Checks coverage across every declared review dimension.

## Reusable lessons

1. Prefer operational constraints over adjectives such as “professional.”
2. Use observable acceptance criteria.
3. Parameterize only values that genuinely vary across runs.
4. Keep examples consistent with the declared output contract.
5. Define an insufficiency, escalation, or recovery path for risky scenarios.

## Archived ranking template

| Rank | Prompt | Scenario | Historical score | Grade | Main gap |
|---:|---|---|---:|---|---|
| 1 | customer-service | Customer support | 92 | S | — |
| 2 | construction-cost | Cost review | 91 | S | Missing one pricing boundary example |
| 3 | rag-agent | RAG | 90 | S | Missing conflicting-source example |
| 4 | legal-contract | Contract review | 89 | A | Example covers only part of the schema |
| 5 | coding-agent | Code review | 88 | A | Single-language example |

This table is an archived teaching artifact, not an executed benchmark leaderboard.
