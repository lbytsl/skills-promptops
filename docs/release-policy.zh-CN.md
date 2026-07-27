# 发布策略

[English](release-policy.md) · 简体中文

PromptOps 使用语义化版本。`SKILL.md` 路由、评分权重、Schema 字段或 verdict 语义变化都属于接口变更。

## 发布门禁

每次 Release 必须：

1. 通过 Skill frontmatter 验证；
2. 校验 Markdown 本地链接和 JSONL 语法；
3. 运行全部公开 fixtures，并保存结果与运行配置；
4. 说明新增、修复、兼容性影响和迁移方式；
5. 对评分规则变化提供前后对比，禁止静默改变历史分数。

## 版本策略

- Patch：文档澄清、等价措辞、无接口行为变化的修复。
- Minor：向后兼容的新 profile、规则、fixture 或可选字段。
- Major：删除能力、修改既有字段/权重/verdict 语义或破坏旧调用方式。

预发布版本使用 `-alpha`、`-beta`、`-rc`。`main` 保持可用，实验性规则进入独立分支或显式标注的 reference。

## Release 内容

Release 附带源代码、可直接安装的 `promptops` Skill 包、变更摘要、验证记录和已知限制。不要发布没有运行配置的“排行榜”。
