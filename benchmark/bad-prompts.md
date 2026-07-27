# Failed Prompt Examples

English · [简体中文](bad-prompts.zh-CN.md)

> Legacy teaching examples. Use `dataset.jsonl` and the current rubric for machine-readable evaluation. Historical scores below came from the retired rubric.

## 1. Vague customer-support prompt

```text
You are a customer-support agent. Help users solve problems. Be professional and friendly.
```

Core failure: the task, inputs, constraints, output, and acceptance criteria are undefined, so the model must guess the operating policy.

## 2. Medical-record review that asks for everything

```text
Review this medical record for formatting, completeness, diagnostic evidence,
medication quality, insurance compliance, dispute risk, improvements, and a score.
```

Core failure: many high-stakes tasks are compressed into one instruction with no authoritative evidence, anti-fabrication boundary, output contract, or human-review path.

## 3. Legal advice without grounding

```text
You are a lawyer. Analyze the legal risks in this contract clause and suggest revisions.
Clause: {contract_clause}
```

Core failure: no jurisdiction, authoritative source, uncertainty rule, output contract, or escalation boundary is defined.

## 4. Contradictory weekly report

```text
Create a detailed weekly report with deep analysis of all work, technical details,
and business impact, limited to 200 words.
```

Core failure: “detailed,” “all work,” and “deep analysis” conflict with the hard length limit, and no priority or compression rule resolves the conflict.

## 5. RAG assistant vulnerable to injection

```text
You are a knowledge-base assistant. Analyze the user question and retrieved snippets,
then provide a complete answer.
Context: {context}
Question: {question}
```

Core failure: retrieved and user content can override instructions; the evidence boundary, empty retrieval, conflicting sources, citations, and anti-fabrication behavior are missing.

## 6. Scope drift in construction review

```text
You are a cost engineer. Review this bill of quantities for omissions and pricing risk,
recommend a bid price, and predict the probability of winning.
```

Core failure: the task drifts from document review into pricing strategy and unsupported prediction, with no evidence or authority boundary.

## Summary

| Case | Profile | Primary failure |
|---:|---|---|
| 1 | General | Undefined contracts and boundaries |
| 2 | High stakes | Overloaded task and no grounding controls |
| 3 | High stakes | Missing jurisdiction, sources, and review path |
| 4 | General | Unresolved instruction conflict |
| 5 | RAG | Injection and fabrication exposure |
| 6 | High stakes | Scope drift and unsupported prediction |

These examples are teaching contrasts. Runtime claims require the protocol in [README.md](README.md).
