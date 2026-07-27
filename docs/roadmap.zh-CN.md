# Roadmap

[English](roadmap.md) · 简体中文

## v0.2 — Foundation

- 标准化 Skill metadata 与渐进加载结构；
- 增加可靠性维度与场景 profiles；
- 建立首批机器可读 fixtures；
- 补齐开源治理和发布文档。

退出条件：Skill 校验通过，核心链接有效，每个支持意图至少有一个示例。

## v0.3 — Community Dataset

- 建立 Prompt failure taxonomy；
- 扩展至 50+ 中英双语 fixtures；
- 为 RAG、Agent、Coding、Structured Output 分别建立子集；
- 引入 fixture 贡献审查清单。

退出条件：每条 fixture 有来源、许可证、预期判定与理由；至少 5 名外部贡献者。

## v0.4 — Reproducible Evaluation

- 固定模型、参数、重复次数和统计口径；
- 分离静态质量分、任务成功率、稳定性与安全失败率；
- 发布首份跨模型报告和原始运行记录。

退出条件：第三方可以从公开说明复现核心结果。

## v0.5 — Prompt Quality Spec RC

- 发布 JSON Schema 与规范术语；
- 收集 Agent/框架维护者反馈；
- 明确兼容性和扩展机制。

## v1.0 — Open Standard Skill

- 稳定输入输出契约；
- 完整迁移指南与长期版本策略；
- Prompt Quality Spec 1.0；
- 至少两个外部 Agent/框架集成示例。
