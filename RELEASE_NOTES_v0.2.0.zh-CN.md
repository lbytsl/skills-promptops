# PromptOps v0.2.0（简体中文发布说明）

**工程化可靠提示词的开源标准技能。**

这是 PromptOps 的首个公开版本。PromptOps 把提示词当作可测试的工程制品，帮助你对 LLM 应用与 AI Agent 的提示词进行评测、改进、对比与测试，而不只是生成更多文本。

## 核心亮点

- **定位升级** —— 从“提示词生成”转向 **Prompt Quality（提示词质量）** 与 **AI Agent Reliability（智能体可靠性）**。
- **Agent 原生元数据** —— 渐进式 Skill 加载，并提供可选的 OpenAI Codex UI 适配器。
- **可靠性评分规范** —— 覆盖稳定性、幻觉、指令冲突、场景适配、模型/工具适配。
- **Benchmark fixtures** —— 机器可读的 `dataset.jsonl`，配套可复现协议。
- **开源治理** —— 路线图、发布策略、安全策略、贡献指南与平台无关接入文档。
- **中英双语** —— 完整的中英文 README。

## 包含内容

| 路径 | 用途 |
|---|---|
| `SKILL.md` | 可移植的提示词工程工作流：评测 → 改进 → 对比 → 测试 → 发布 |
| `references/` | 评分规范、测试方法、对比方法、Schema、访谈模式 |
| `examples/` | RAG 智能体、编码智能体、客服、法务合同示例 |
| `benchmark/` | `dataset.jsonl` fixtures 与评测协议 |
| `agents/` | 可选的 OpenAI Codex 元数据适配器 |
| `docs/` | 路线图、发布策略、接入指南、贡献指南 |

## 兼容性

纯 Markdown 核心，**无专有运行时依赖**。兼容 Claude Code、OpenAI Codex、Trae、WorkBuddy 以及任何能发现 `SKILL.md` 的智能体。

## 安装

```bash
git clone https://github.com/lbytsl/skills-promptops.git
```

将 `promptops` 目录链接到你的 Agent 的 Skill 位置，或将 `SKILL.md`（及其相对 `references/`）作为项目指令加载。

## 许可证

Apache License 2.0
