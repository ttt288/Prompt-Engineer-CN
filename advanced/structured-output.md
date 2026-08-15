# Structured Output

结构化输出保证后端可解析。能用 API 级 JSON schema 或 function calling 时，优先用 API 约束；Prompt 约束作为第二层。

## JSON 模板

```text
你是中文信息抽取 API。只输出合法 JSON，不要 Markdown，不要解释。

Schema:
{
  "intent": "求职 | 内容创作 | 电商 | 学习 | 编程 | 其他",
  "entities": {
    "platform": "string | null",
    "topic": "string | null",
    "deadline": "string | null"
  },
  "confidence": "number, 0 到 1"
}

用户输入：
{{input}}
```

## 防偏移规则

- 字段名必须完全一致。
- 缺失值用 `null`，不要省略字段。
- 不要输出注释、代码块、解释、前后缀。
- 解析失败时重试，并把错误反馈给模型修正。
