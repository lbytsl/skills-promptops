---
name: promptops
version: 0.2.0
display_name: PromptOps 提示词质量与可靠性
display_name_en: PromptOps
description: Evaluate, improve, compare, and test prompts for reliable LLM applications and AI agents. Use when a user asks to audit prompt quality, diagnose hallucination or instruction-conflict risks, optimize a system prompt, compare prompt versions, generate prompt test cases, define release gates, or engineer prompts for RAG, agents, coding, structured output, and other LLM workflows. Also use to create a new prompt when the user needs a production-ready specification rather than simple copywriting.
description_zh: 将提示词视为可测试的工程制品,提供评测、改进、对比、测试与发布门禁的完整工作流,覆盖 RAG、Agent、编码、结构化输出与高风险场景,无专有运行时依赖,兼容 Claude Code、Codex、Trae、WorkBuddy 等智能体。
description_en: Treat prompts as testable engineering artifacts. Provides evaluate/improve/compare/test/release workflows for RAG, agents, coding, and structured-output tasks, with no proprietary runtime dependency.
---

# PromptOps

Treat prompts as testable engineering artifacts. Optimize for task success, stability, safety, traceability, and maintainability—not eloquence alone.

## Route the request

Infer the primary intent from the user's artifact and requested outcome:

| Intent | Signals | Action |
|---|---|---|
| `design` | Goal exists; no usable prompt | Clarify essentials, then produce a prompt specification |
| `evaluate` | Prompt supplied; asks for score, review, or risks | Score with evidence and diagnose |
| `improve` | Prompt supplied; asks to fix, rewrite, or harden | Evaluate, revise, and report material changes |
| `compare` | Two or more versions supplied | Compare on one shared rubric and detect regressions |
| `test` | Asks for cases, validation, regression, or release readiness | Build a test suite and release gate |

If multiple intents are explicit, compose them in this order: evaluate → improve → compare → test. If intent is genuinely ambiguous, ask one routing question; otherwise proceed.

## Gather only decision-critical context

Use progressive clarification. Never require a form.

1. Infer task, audience, input shape, output consumer, and risk level from supplied context.
2. State reasonable assumptions briefly.
3. Ask at most three questions only when answers materially change the result. Prioritize:
   - What must the model accomplish?
   - What evidence or source may it use?
   - What failure is unacceptable?
4. Offer a recommended default and allow “use defaults.”
5. For high-stakes legal, medical, financial, security, or compliance work, require the authoritative source and escalation boundary; never invent them.

For detailed question patterns, read [references/interview.md](references/interview.md) only when designing a prompt from sparse requirements.

## Classify the context

Select the applicable profile before evaluating or designing:

- **General**: ordinary generation, extraction, transformation, or conversation.
- **RAG**: retrieved context is the evidence boundary; require citation and insufficiency behavior.
- **Agent**: tools or actions create side effects; require permissions, confirmation, recovery, and stop conditions.
- **Coding**: require repository context, verification commands, scope control, and change reporting.
- **Structured output**: require an explicit schema, null/error behavior, and parseability.
- **High stakes**: require provenance, uncertainty, refusal/escalation, and human review.

## Evaluate prompt quality

Read [references/rubric.md](references/rubric.md) before scoring. Use one rubric for all compared versions. Quote exact prompt evidence; missing evidence earns no inferred credit.

Always assess these reliability dimensions in addition to structural completeness:

- task clarity and success criteria;
- output contract and machine-readability;
- constraint coverage and instruction priority;
- grounding, traceability, and hallucination controls;
- output stability under input variation;
- scenario and model/tool fit;
- injection resistance, permissions, and failure recovery where applicable;
- testability and maintainability.

Return:

1. verdict, score, confidence, and release recommendation;
2. evidence-based scorecard;
3. blocking risks before refinements;
4. prioritized fixes with expected impact;
5. revised prompt only when requested or implied.

Do not claim empirical stability from static review. Label it `untested` until cases have been executed.

## Improve without changing intent

Preserve the user's goal, authority boundary, language, and downstream interface. Resolve conflicts by declaring an instruction hierarchy. Add missing behavior for absent evidence, invalid input, uncertainty, and tool failure. Prefer observable requirements over vague adjectives.

Return a change log mapping each material edit to the risk it addresses. Flag assumptions rather than silently expanding scope.

## Compare versions

Read [references/compare.md](references/compare.md). Verify that versions share the same task baseline. Compare structure, capabilities, score deltas, risks, and compatibility. A higher aggregate score cannot override a new blocking failure. Recommend `baseline`, `candidate`, `merge`, or `blocked`, with migration notes when interfaces change.

## Test and gate release

Read [references/testing.md](references/testing.md). Create typical, boundary, adversarial, and—when relevant—compliance cases. Prefer deterministic assertions, then golden outputs, then a disclosed judge rubric. Separate static review from execution results.

A release passes only when:

- every blocking assertion passes;
- no previously passing regression becomes a failure;
- the declared pass-rate threshold is met;
- high-stakes prompts have an explicit human-review path.

## Design a new prompt

Produce the smallest complete specification that fits the profile:

1. role and authority;
2. objective and ordered tasks;
3. context and allowed evidence;
4. input contract;
5. constraints, priority, and failure behavior;
6. output contract;
7. acceptance criteria;
8. examples only when they resolve ambiguity.

Then run a static self-evaluation and clearly distinguish the score from an executed benchmark result.

## Use bundled resources

- Read [references/rubric.md](references/rubric.md) for scoring anchors and reliability gates.
- Read [references/testing.md](references/testing.md) for test design and release decisions.
- Read [references/compare.md](references/compare.md) for version comparison.
- Read [references/schema.md](references/schema.md) only for structured integrations.
- Read [references/interview.md](references/interview.md) only for sparse design requests.
- Use [examples/](examples/) as patterns, not authoritative domain sources.
- Use [benchmark/dataset.jsonl](benchmark/dataset.jsonl) for reproducible evaluation fixtures.

Follow the user's language. Lead with the decision. Keep outputs compact unless the user asks for the full audit.
