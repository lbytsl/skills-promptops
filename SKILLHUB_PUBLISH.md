# SkillHub 发布清单（PromptOps v0.2.0）

本文件汇总在 [SkillHub](https://skillhub.cn) 上架 PromptOps 所需的全部元信息与操作步骤。安装包与图标由发布流程生成，位于 `release-assets/`。

## 一、待填写的元信息（直接复制到 SkillHub 发布表单）

| 字段 | 内容 |
|---|---|
| 技能名称 | **PromptOps** |
| 一句话简介（≤20 字） | 工程化可靠提示词的开源标准技能 |
| 详细描述（100–300 字） | PromptOps 是一套面向 LLM 应用与 AI Agent 的开源提示词工程标准技能。它将提示词视为可测试的工程制品，提供评测（质量与风险审计）、改进（意图保留式优化）、对比（共享基线版本差分）、测试（典型/边界/对抗/回归用例与发布门禁）的完整工作流。核心为纯 Markdown，无专有运行时依赖，兼容 Claude Code、OpenAI Codex、Trae、WorkBuddy 等主流智能体。覆盖 RAG、Agent、编码、结构化输出与高 stakes 场景的可靠性维度（稳定性、幻觉、指令冲突、场景与模型/工具适配）。附中英文文档、可靠性评分规范与可复现 Benchmark fixtures。 |
| 分类标签 | 开发者工具、AI 效率、提示词工程 |
| 图标 | `release-assets/promptops-icon-512.png`（512×512 PNG，已生成） |
| 权限声明 | 无特殊权限。本技能为纯 Markdown 内容技能，不访问文件系统、网络或执行命令；其能力由宿主智能体在对话中调用。 |
| 使用说明 | 将技能目录放入 Agent 的 skills 路径，或把 `SKILL.md` 作为项目/系统指令加载并保持 `references/` 相对路径可读。自然语言提出“审计/改进/对比/测试某提示词”即可触发对应工作流。 |
| 版本 | v0.2.0 |
| 开源协议 | Apache License 2.0 |
| 源码仓库 | https://github.com/lbytsl/skills-promptops |

## 二、安装包

- 文件：`release-assets/promptops-skillhub-v0.2.0.zip`
- 内容：`SKILL.md` + `references/` + `examples/` + `benchmark/` + `agents/` + `LICENSE` + `README.md` / `README.zh-CN.md`
- 解压后即为可直接放入 skills 目录的 `promptops/` 技能包。

## 三、上架步骤

1. 访问 [skillhub.cn](https://skillhub.cn)，右上角点击 **发布团队 Skill**（首次需完成开发者注册/邮箱验证与实名认证）。
2. 选择发布类型（免费版即可）。
3. 填写上方“待填写的元信息”各字段，上传图标 `promptops-icon-512.png`。
4. 上传安装包 `promptops-skillhub-v0.2.0.zip`。
5. 提交审核。审核链路：平台安全审核 →（企业账号）管理员审核，通常 1–3 个工作日。
6. 审核通过后，在【技能列表】点击 **上架**。随后即可在 WorkBuddy 技能入口搜索到 PromptOps。

## 四、发布后建议

- 及时回复用户反馈；保持至少每 2 个月一次的更新节奏。
- 同步维护 GitHub Release 与 SkillHub 版本号一致（当前 v0.2.0）。
- 配合 90 天 GitHub Stars 增长计划，在小红书/抖音/CSDN/公众号多平台分发推广卡片。
