# PromptOps v0.2.0

**The open standard skill for engineering reliable prompts.**

This is the first public release of PromptOps. PromptOps treats prompts as testable engineering artifacts and helps you evaluate, improve, compare, and test prompts for reliable LLM applications and AI agents — instead of just generating more text.

## Highlights

- **Repositioned scope** — from prompt generation to **Prompt Quality** and **AI Agent Reliability**.
- **Agent-native metadata** — progressive Skill loading and an optional OpenAI Codex UI adapter.
- **Reliability rubric** — covers stability, hallucination, instruction conflict, scenario fit, and model/tool fit.
- **Benchmark fixtures** — a machine-readable `dataset.jsonl` with a documented reproduction protocol.
- **Open governance** — roadmap, release policy, security policy, contribution guide, and platform-neutral integration docs.
- **Bilingual** — full English and Simplified Chinese READMEs.

## What's included

| Path | Purpose |
|---|---|
| `SKILL.md` | Portable prompt-engineering workflow: evaluate → improve → compare → test → release |
| `references/` | Rubric, testing method, comparison method, schema, and interview patterns |
| `examples/` | RAG agent, coding agent, customer service, legal contract patterns |
| `benchmark/` | `dataset.jsonl` fixtures and the evaluation protocol |
| `agents/` | Optional OpenAI Codex metadata adapter |
| `docs/` | Roadmap, release policy, integrations, contribution guide |

## Compatibility

Plain-Markdown core with **no proprietary runtime dependency**. Works with Claude Code, OpenAI Codex, Trae, WorkBuddy, and any agent that can discover `SKILL.md`.

## Install

```bash
git clone https://github.com/lbytsl/skills-promptops.git
```

Link the `promptops` directory into your agent's Skill location, or load `SKILL.md` (with its relative `references/`) as project instructions.

## License

Apache License 2.0
