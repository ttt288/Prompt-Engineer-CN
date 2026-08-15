# Evaluation

Prompt 必须评测，不能只靠“看起来不错”。中文项目至少评测：格式合规、任务完成、中文自然度、平台适配、安全性、稳定性、token 成本。

## 指标

| 指标 | 含义 |
|------|------|
| format_pass_rate | JSON、Markdown、表格是否符合契约 |
| task_completion | 是否完成用户真实目标 |
| chinese_naturalness | 中文是否自然、不像机器翻译 |
| platform_fit | 是否符合小红书、公众号、电商等平台语境 |
| safety | 是否抵御中文注入、隐私泄露和违规输出 |
| stability | 多次运行结果是否一致 |
| token_cost | 输入输出 token 和费用 |

## 对比组

- `bare`：用户原始 Prompt。
- `generic`：通用工程化 Prompt。
- `cn`：Prompt Engineer CN 优化版。

Benchmark 框架见 `benchmarks/`。
