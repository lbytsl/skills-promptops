# Release Policy

English · [简体中文](release-policy.zh-CN.md)

PromptOps follows Semantic Versioning. Changes to `SKILL.md` routing, scoring semantics, schema fields, or verdict meaning are interface changes.

## Release gate

Every release must:

1. pass Skill frontmatter validation;
2. validate local Markdown links, YAML, and JSONL;
3. run all public fixtures and retain results plus configuration;
4. document additions, fixes, compatibility impact, and migration steps;
5. publish before/after evidence for scoring changes and never alter historical scores silently.

## Version policy

- Patch: documentation clarification or behavior-equivalent fixes.
- Minor: backward-compatible profiles, rules, fixtures, or optional fields.
- Major: removed capabilities, changed existing fields/weights/verdict semantics, or broken invocation behavior.

Pre-releases use `-alpha`, `-beta`, and `-rc`. Keep `main` usable and place experimental rules behind explicit references or branches.

## Release artifacts

Include source, an installable `promptops` Skill package, change summary, validation record, and known limitations. Never publish a leaderboard without its runtime configuration.
