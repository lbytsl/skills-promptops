# AI Agent Integration Guide

English · [简体中文](integrations.zh-CN.md)

PromptOps separates a portable core from optional platform adapters.

## Portable core

The portable core consists of:

```text
SKILL.md
references/
examples/
benchmark/
```

`SKILL.md` uses standard Markdown, YAML frontmatter with only `name` and `description`, relative file links, and no mandatory tool calls. Any AI system that can load instructions and related files can use the core.

## Integration levels

### 1. Native Skill discovery

If a product supports directory-based Skills, install or link the whole repository as a folder named `promptops`. The agent should discover `SKILL.md` and load references only when the workflow requires them.

### 2. Project instructions

If a product supports project rules but not Skills, use `SKILL.md` as the project instruction entry point. Preserve access to the adjacent `references/` directory. Avoid copying every reference into the always-on context.

### 3. Manual or API context

For chat products and custom Agent runtimes, provide `SKILL.md` as a system/developer instruction and resolve reference files through your retrieval or file-loading layer. Route natural user requests to PromptOps based on the frontmatter description.

### 4. Embedded methodology

Applications can integrate only the structured contract, rubric, testing method, or benchmark fixtures. PromptOps does not require its full conversational interaction model.

## Platform notes

### Claude Code

Use the current Claude Code mechanism for project/user Skills or persistent project instructions. Install the complete directory rather than pasting only the prompt text so relative references remain available.

### OpenAI Codex

Install the directory as a Skill named `promptops`. `agents/openai.yaml` is an optional OpenAI/Codex UI adapter; it does not affect the portable core.

### Trae and WorkBuddy

Use their current custom Skill, rule, knowledge, or project-instruction mechanism. If automatic directory discovery is unavailable, load `SKILL.md` as the entry point and expose `references/` through files or retrieval.

### Custom agents

Index the frontmatter `name` and `description` for routing. After a match, load the body of `SKILL.md`; load only the reference explicitly required by the selected operation. This preserves the progressive-disclosure design and reduces token usage.

## Compatibility promise

PromptOps guarantees that the portable core will remain:

- readable as plain text;
- independent of a specific model vendor;
- free of mandatory proprietary tools or APIs;
- navigable through relative paths;
- versioned when behavior or contracts change.

It does not guarantee identical automatic discovery, instruction precedence, tool access, or output behavior across products. Platform-specific installation paths should always follow the current vendor documentation.
