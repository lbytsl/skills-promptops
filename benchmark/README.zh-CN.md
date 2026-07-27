# PromptOps Benchmark

[English](README.md) · 简体中文

本目录是一组开放的 Prompt 失败模式 fixtures，而不是“某个 Prompt 在所有情况下最好”的排行榜。

## 数据集

`dataset.jsonl` 每行包含一个 JSON 对象：

- `id`：稳定标识符；
- `profile`：general、rag、agent、coding、structured_output 或 high_stakes；
- `risk`：low、medium、high 或 critical；
- `prompt`：被评估的 Prompt；
- `expected_verdict`：blocked、needs_work 或 candidate；
- `failure_labels`：预期失败分类；
- `rationale`：人工裁决理由；
- `source_type`：synthetic 或 anonymized_real；
- `license`：复用许可。

## 评估赛道

1. **静态审查**：将检测到的 verdict 和失败标签与 fixtures 比较。
2. **运行时任务成功**：执行已声明的输入和确定性断言。
3. **稳定性**：重复运行，分别报告 Schema 有效率、语义通过率和分歧率。
4. **回归**：用相同基线测试套件比较候选版本。

不得把这些赛道合并成没有清晰标签的单一“质量分”。

## 复现要求

公开数据集版本、模型标识、完整 system/developer context、工具配置、采样参数、重复次数、Judge rubric/版本、原始输出和聚合代码。存在争议或高风险的案例应至少由两名评审者裁决。

已有 Markdown 案例用于人类教学。只有带有明确协议的结构化 fixtures 才能用于 Benchmark 声明。
