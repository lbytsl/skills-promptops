# 为 PromptOps 贡献

[English](CONTRIBUTING.md) · 简体中文

感谢你帮助 Prompt Engineering 从经验写作走向可验证的工程实践。

## 可以贡献什么

- 带真实失败模式的匿名化 Prompt fixture；
- RAG、Agent、Coding、结构化输出或高风险场景规则；
- 更清晰且可复现的评分锚点、断言与 benchmark 协议；
- 文档修正、翻译和兼容性反馈。

请勿提交私密 Prompt、客户数据、未授权内容或无法公开许可证的数据。

## 贡献流程

1. 先搜索 Issue，较大方法论改动请先发 RFC。
2. 每个规则变更至少添加一个 `benchmark/dataset.jsonl` fixture，说明旧行为为何失败、新行为如何判定。
3. 保持 `SKILL.md` 精炼；详细知识放入直接关联的 `references/`，避免重复。
4. 运行 Skill 验证，并人工检查所有 Markdown 链接和 JSONL 行。
5. Pull Request 说明问题、证据、兼容性影响和验证方式。

## Fixture 最低要求

每条数据必须有稳定 `id`、场景、风险等级、输入 Prompt、预期 verdict、失败标签和理由。高风险内容必须匿名化，并明确它是合成数据还是真实数据的脱敏版本。

## 设计原则

- 评价行为，不评价文风。
- 静态推断与实际运行结果必须分开。
- 聚合分数不得掩盖阻塞风险。
- 不为单一模型、平台或供应商写隐藏假设。
- 修改保持向后兼容；破坏性变更遵循 Release Policy。

参与本项目即表示你同意遵守 [行为准则](CODE_OF_CONDUCT.zh-CN.md)，并按 Apache-2.0 许可贡献内容。
