# 报告模板

输出时使用以下结构。先 Markdown，后 YAML。正文语言与用户一致（默认中文）。
维度 / 子项 ID 用英文（来自评分卡）；显示名可用中文。

评分层级：`类型 → 维度 → 子项`。子项先打分，再平均得到维度分，再按权重得到总分。

---

## Markdown

```markdown
# Grader 报告 · {type_label}

**范围：** {paths_or_scope}
**类别：** `{category}` · **类型：** `{type_id}`
**总分：** {total}/100 · **等级：** {grade}

## 总评

{2–4 句：结论、最强项、最致命短板；可点名最差子项}

## 维度分数

| 维度 | 权重 | 分数 | 一句话依据 |
|------|------|------|------------|
| {dimension_name} | {w} | {0–10 或 N/A} | {证据摘要} |

## 子项分数

### {dimension_name} (`{dimension_id}`) · {dim_score}/10

| 子项 | 分数 | 依据 |
|------|------|------|
| {sub_name} (`{sub_id}`) | {0–10 或 N/A} | {路径/符号 + 短说明} |

（每个非 N/A 维度都输出一张子项表）

## 优点

- **[{dimension}/{sub}]** {具体优点 + 证据}
- …

## 缺点

- **[{dimension}/{sub}]** {具体问题 + 证据}
- …

## 改进建议

### P0（立刻改）
1. **{标题}** — 影响：{dimension}/{sub}。{做什么}。预期：{提分说明}

### P1（近期改）
1. …

### P2（可选）
1. …
```

若某优先级无项，写「无」。

多类型体检时：每种类型各出一份完整报告，最后追加一节：

```markdown
## 综合总评

| 类型 | 总分 | 等级 |
|------|------|------|
| `{type_id}` | {total} | {grade} |

{一段话串联各类型，不编造未评类型的分数}
```

---

## YAML

紧跟 Markdown 之后输出（fenced `yaml`）：

```yaml
scorecard:
  skill: grader
  category: {category}
  type: {type_id}
  scope: [{path}, ...]
  total: {0-100}
  grade: {S|A|B|C|D}
  dimensions:
    {dimension_id}:
      score: {0-10|null}
      weight: {number}
      note: "{rollup evidence}"
      subs:
        {sub_id}:
          score: {0-10|null}
          note: "{evidence}"
  strengths:
    - dimension: {id}
      sub: {id|null}
      text: "{...}"
  weaknesses:
    - dimension: {id}
      sub: {id|null}
      text: "{...}"
  actions:
    - priority: P0
      title: "{...}"
      dimensions: [{id}]
      subs: [{id}]
      detail: "{...}"
```

`null` = N/A。维度分 = 其非 null 子项的算术平均。总分仅基于非 null 维度按权重归一。
