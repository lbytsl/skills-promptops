# AI Agent 接入指南

[English](integrations.md) · 简体中文

PromptOps 将跨平台核心与可选平台适配器分离。

## 通用核心

```text
SKILL.md
references/
examples/
benchmark/
```

`SKILL.md` 使用标准 Markdown，YAML frontmatter 仅包含 `name` 和 `description`，使用相对文件路径，不依赖强制工具调用。任何可以加载指令和相关文件的 AI 系统都能使用核心能力。

## 接入层级

### 1. 原生 Skill 发现

如果产品支持目录型 Skills，将完整仓库安装或链接为名为 `promptops` 的目录。Agent 应发现 `SKILL.md`，并只在对应工作流需要时加载 references。

### 2. 项目指令

如果产品支持项目规则但不支持 Skills，将 `SKILL.md` 作为项目指令入口，并保留对相邻 `references/` 的访问。不要把所有 reference 都复制到常驻上下文。

### 3. 手动或 API 上下文

对于聊天产品和自定义 Agent runtime，将 `SKILL.md` 作为 system/developer instruction，通过检索或文件加载层解析 references。使用 frontmatter description 对用户自然语言请求进行路由。

### 4. 方法论嵌入

应用也可以只集成结构化契约、评分规范、测试方法或 benchmark fixtures，而不采用完整的对话交互方式。

## 平台说明

### Claude Code

使用当前版本支持的项目级/用户级 Skill 或持久项目指令机制。安装完整目录而不是只粘贴 Prompt，以保证相对 references 可读。

### OpenAI Codex

将目录安装为名为 `promptops` 的 Skill。`agents/openai.yaml` 是可选的 OpenAI/Codex UI 适配器，不影响通用核心。

### Trae 与 WorkBuddy

使用当前版本提供的自定义 Skill、规则、知识或项目指令机制。如果不能自动发现目录，则以 `SKILL.md` 为入口，并通过文件或检索暴露 `references/`。

### 自定义 Agent

索引 frontmatter 中的 `name` 与 `description` 完成路由。匹配后加载 `SKILL.md` 正文，并只加载所选操作明确需要的 reference，从而保留渐进式披露并降低 token 消耗。

## 兼容承诺

PromptOps 保证通用核心：

- 可作为纯文本读取；
- 不依赖单一模型厂商；
- 不强制依赖专有工具或 API；
- 可通过相对路径导航；
- 行为或契约改变时遵循版本管理。

PromptOps 不保证不同产品具有完全相同的自动发现、指令优先级、工具访问或输出行为。平台安装路径应以厂商当前文档为准。
