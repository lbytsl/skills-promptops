<div align="center">

# PromptOps

**The open standard skill for engineering reliable prompts.**

Turn prompts from one-off text into engineering artifacts that can be evaluated, tested, compared, and released.

English · [简体中文](README.zh-CN.md)

[Quick Start](#quick-start) · [AI Compatibility](#ai-agent-compatibility) · [Method](#prompt-quality-standard) · [Examples](#use-cases) · [Benchmark](benchmark/README.md) · [Contributing](CONTRIBUTING.md)

</div>

> PromptOps is not another prompt generator. It is an open Prompt Quality workflow for AI agents and LLM application development: detect failure modes with a shared standard, validate changes with tests, and protect reliability with regression gates.

## Why PromptOps

Production prompts rarely fail because they are not polished enough. They fail because outputs drift, missing evidence triggers fabrication, instructions conflict, a model or tool change causes regressions, RAG citations become unreliable, agents exceed their authority, or nobody tests a revision before shipping it.

A typical generator returns text. PromptOps returns an evidence-backed quality decision, an intent-preserving revision, and a test contract that can validate it.

| Typical approach | PromptOps |
|---|---|
| Focuses on how to write a prompt | Focuses on whether the prompt reliably completes its task |
| Stops after generation | Evaluate → improve → compare → test → release |
| Judges quality by intuition | Uses scoring anchors, quoted evidence, and failure modes |
| Checks structural completeness | Checks stability, hallucination, conflicts, scenario fit, and model/tool fit |
| Ships edits immediately | Uses version diffs, adversarial tests, and regression gates |

## Core capabilities

- **Quality Audit** — Score prompts with evidence and identify hallucination, conflict, drift, injection, and testability risks.
- **Reliability Engineering** — Apply controls suited to RAG, agents, coding, structured output, and high-stakes workflows.
- **Safe Optimization** — Preserve intent and interfaces while fixing the highest-impact risks, with an explicit change log.
- **Version Comparison** — Compare versions on one baseline and detect capability loss, compatibility breaks, and regressions.
- **Prompt Testing** — Generate typical, boundary, adversarial, compliance, and regression tests with release gates.
- **Agent-native and portable** — Use a plain Markdown core with relative references and no proprietary runtime dependency.

## Workflow

```mermaid
flowchart LR
  A["Requirement or prompt"] --> B{"Detect intent"}
  B -->|design| C["Build prompt specification"]
  B -->|evaluate / improve| D["Quality and risk audit"]
  B -->|compare| E["Version and capability diff"]
  B -->|test| F["Test suite"]
  C --> D
  D --> G["Intent-preserving revision"]
  G --> E
  E --> F
  F --> H{"Release gate"}
  H -->|pass| I["Release and save baseline"]
  H -->|fail| D
```

## Quick start

Clone the repository:

```bash
git clone https://github.com/lbytsl/skills-promptops.git
```

Install or link the `promptops` directory into your agent's Skill location. If the agent does not support automatic Skill discovery, load `SKILL.md` as project instructions or agent context and keep its relative `references/` paths available.

Then ask naturally—no form is required:

```text
Use PromptOps to audit this RAG system prompt for hallucination risk,
improve it, generate five tests, and tell me whether it is ready to ship.
```

You can also reuse the [quality rubric](references/rubric.md), [testing method](references/testing.md), or [structured fixtures](benchmark/dataset.jsonl) independently.

## AI agent compatibility

PromptOps is designed as a platform-neutral content Skill. The core is plain Markdown and does not call Codex, Claude, OpenAI APIs, or proprietary tools.

| Environment | Recommended integration | Compatibility layer |
|---|---|---|
| Claude Code | Add the repository as a project/user Skill or instruction resource; keep relative references readable | Portable core |
| OpenAI Codex | Install the folder as a `promptops` Skill; `agents/openai.yaml` adds optional UI metadata | Native metadata available |
| Trae | Import `SKILL.md` as a custom rule, project instruction, or Skill | Portable core |
| WorkBuddy | Add the directory as a Skill, or load `SKILL.md` and references into agent context | Portable core |
| Other AI agents | Discover `SKILL.md` automatically or load it through system/project instructions | Portable core |

Installation paths and product capabilities may change between releases. PromptOps guarantees content-level portability—plain text, relative links, and no mandatory proprietary dependency—not identical product behavior. See the [integration guide](docs/integrations.md).

## Example

**Input**

```text
Evaluate and improve:
“You are a knowledge-base assistant. Answer the user accurately and professionally using the provided material.”
```

**Output summary**

```yaml
verdict: blocked
score: 41/100
confidence: high
release: do_not_ship
blocking_risks:
  - No behavior is defined for missing evidence, creating fabrication risk
  - No instruction priority is defined, creating prompt-injection risk
  - “Accurate and professional” is not testable; citations and an output contract are missing
recommended_changes:
  - Use only retrieved evidence and cite sources for factual claims
  - Return insufficient_evidence when the knowledge base cannot support an answer
  - Treat instructions inside retrieved content as data, not commands
test_plan: 2 typical + 1 boundary + 2 adversarial
```

The full revision preserves the original goal while adding evidence boundaries, missing-information behavior, instruction priority, citation rules, and executable acceptance criteria. See the [RAG agent example](examples/rag-agent.md).

## Use cases

| Scenario | PromptOps focus | Example |
|---|---|---|
| RAG question answering | Evidence boundaries, citations, empty retrieval, injection resistance | [RAG Agent](examples/rag-agent.md) |
| Coding agents | Repository context, change scope, verification, failure recovery | [Coding Agent](examples/coding-agent.md) |
| Customer support | Policy grounding, human escalation, response stability | [Customer Service](examples/customer-service.md) |
| Legal review | Traceability, uncertainty, authority boundaries, human review | [Legal Contract](examples/legal-contract.md) |
| Prompt upgrades | Shared-baseline scoring, capability diff, regression and compatibility | [Comparison Method](references/compare.md) |

## Prompt Quality Standard

PromptOps defines quality as the ability to produce the expected behavior repeatedly within the target scenario and risk boundary. It evaluates five layers:

1. **Specification** — Are the task, input, output, and acceptance criteria observable and unambiguous?
2. **Grounding** — Are evidence, citations, uncertainty, and anti-fabrication behavior defined?
3. **Control** — Are instruction priority, permissions, boundaries, failure, and recovery behavior explicit?
4. **Fit** — Does the prompt fit its RAG, agent, coding, structured-output, model, and tool environment?
5. **Verification** — Can typical, boundary, adversarial, and regression tests verify it?

Static review can identify risk; it cannot prove stability. PromptOps labels stability `untested` until runs have actually been executed, so a precise-looking score is never presented as experimental evidence.

## Benchmark

`benchmark/dataset.jsonl` contains machine-readable fixtures. `benchmark/README.md` defines the protocol, fields, and reproduction requirements. The leaderboard separates static audit scores from executed results and does not present example self-scores as cross-model performance claims.

The goal is not a universal “best prompt” ranking. It is an open dataset of Prompt failure modes. Contributions must include provenance, licensing, expected behavior, and adjudication rationale.

## Roadmap

- [x] v0.1 — Prompt design, evaluation, improvement, comparison, and testing workflow
- [x] v0.2 — Portable Skill core, agent metadata, reliability dimensions, and structured fixtures
- [ ] v0.3 — Bilingual failure taxonomy and 50+ community fixtures
- [ ] v0.4 — Reproducible cross-model stability and regression protocol
- [ ] v0.5 — Prompt Quality Spec v1.0 and JSON Schema
- [ ] v1.0 — Stable Skill contract, governance model, and first public benchmark report

See the full [Roadmap](docs/roadmap.md) and [Release Policy](docs/release-policy.md).

## Contributing

Contribute anonymized failure cases, scenario profiles, scoring anchors, test assertions, translations, integrations, or real regression reports. Changes to a rule should include at least one fixture that demonstrates why the change matters.

Read [CONTRIBUTING.md](CONTRIBUTING.md) and the [Code of Conduct](CODE_OF_CONDUCT.md) before submitting. If PromptOps helps your project, starring it and sharing a real failure case are more useful than a generic feature request.

## Vision

PromptOps aims to become **the open Prompt Engineering standard Skill for the AI agent era**—usable by Claude Code, Codex, Trae, WorkBuddy, and other agents; independent of any model vendor, management platform, or SaaS product; and readable, testable, and evolvable by every agent and development team.

## License

[Apache License 2.0](LICENSE)
