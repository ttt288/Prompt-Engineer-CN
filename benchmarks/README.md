# Benchmark

这个目录用于补齐项目当前最大的缺口：真实 Before / After benchmark 数据。

目标是用同一批中文任务，对比三类 Prompt：

- `bare`：用户原始 Prompt，不做工程化改写。
- `generic`：通用工程化 Prompt，强调角色、约束和输出格式。
- `cn`：Prompt Engineer CN 版，加入中文语境、平台风格、安全边界和本地化评测要求。

建议在 DeepSeek、Qwen、Kimi、GLM 等模型上各跑 3-5 次，统计：

- 格式通过率
- 任务完成度
- 中文自然度
- 平台适配度
- 安全性
- 稳定性
- token 成本

## 文件

```text
benchmarks/
  tasks.jsonl
  prompts/
    bare.md
    generic.md
    cn.md
  run_benchmark.py
  results/
```

## 运行方式

不同模型如果提供 OpenAI-compatible API，可以通过环境变量切换：

```bash
export OPENAI_API_KEY=your-key
export OPENAI_BASE_URL=https://api.example.com/v1
python benchmarks/run_benchmark.py --model deepseek-chat --runs 3
```

输出会写入 `benchmarks/results/`。

## 注意

这个目录目前提供 benchmark 框架和样例任务。真实分数需要实际调用目标模型后生成，不建议在没有实验数据时声称“提升百分比”。
