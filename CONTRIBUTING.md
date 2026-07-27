# Contributing to PromptOps

English · [简体中文](CONTRIBUTING.zh-CN.md)

Thank you for helping Prompt Engineering move from intuition-driven writing to verifiable engineering.

## What to contribute

- Anonymized Prompt fixtures with real failure modes;
- rules for RAG, agents, coding, structured output, or high-stakes scenarios;
- clearer and reproducible scoring anchors, assertions, and benchmark protocols;
- documentation fixes, translations, integrations, and compatibility reports.

Do not submit private prompts, customer data, unlicensed content, or datasets that cannot be redistributed.

## Contribution workflow

1. Search existing issues. Propose substantial methodology changes through an RFC first.
2. Add at least one fixture to `benchmark/dataset.jsonl` for every behavior-changing rule and explain the old failure and expected new behavior.
3. Keep `SKILL.md` concise. Put detailed knowledge in directly linked references and avoid duplication.
4. Validate Skill metadata, Markdown links, YAML, and every JSONL record.
5. Explain the problem, evidence, compatibility impact, and verification in the pull request.

## Fixture requirements

Every fixture needs a stable ID, scenario, risk level, input prompt, expected verdict, failure labels, and rationale. High-risk material must be anonymized and labeled as synthetic or anonymized real-world data.

## Design principles

- Evaluate behavior, not writing style.
- Separate static inference from executed evidence.
- Never let an aggregate score hide a blocking risk.
- Avoid assumptions tied to one model, framework, or vendor.
- Preserve backward compatibility; follow the Release Policy for breaking changes.

By contributing, you agree to the [Code of Conduct](CODE_OF_CONDUCT.md) and license your contribution under Apache-2.0.
