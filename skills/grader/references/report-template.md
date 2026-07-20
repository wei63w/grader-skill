# 报告模板

输出时使用以下结构。先 Markdown，后 YAML。语言与用户一致（默认中文）。

---

## Markdown

```markdown
# Grader 报告 · {type_label}

**范围：** {paths_or_scope}
**类型：** `{type_id}`
**总分：** {total}/100 · **等级：** {grade}

## 总评

{2–4 句：结论、最强项、最致命短板}

## 分数表

| 维度 | 权重 | 分数 | 一句话依据 |
|------|------|------|------------|
| {name} | {w} | {0–10 或 N/A} | {证据摘要，含路径} |

## 优点

- **[{dimension}]** {具体优点 + 证据}
- …

## 缺点

- **[{dimension}]** {具体问题 + 证据}
- …

## 改进建议

### P0（立刻改）
1. **{标题}** — 影响维度：{dims}。{做什么}。预期：{提分说明}

### P1（近期改）
1. …

### P2（可选）
1. …
```

若某优先级无项，写「无」。

---

## YAML

紧跟 Markdown 之后输出（可用 fenced `yaml` 代码块）：

```yaml
scorecard:
  skill: grader
  type: {type_id}
  scope: [{path}, ...]
  total: {0-100}
  grade: {S|A|B|C|D}
  dimensions:
    {dimension_id}:
      score: {0-10|null}
      weight: {number}
      note: "{short evidence}"
  strengths:
    - dimension: {id}
      text: "{...}"
  weaknesses:
    - dimension: {id}
      text: "{...}"
  actions:
    - priority: P0
      title: "{...}"
      dimensions: [{id}]
      detail: "{...}"
```

`null` 表示 N/A。`total` 仅基于非 null 维度按权重归一计算。
