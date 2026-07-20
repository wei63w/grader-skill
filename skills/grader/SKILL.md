---
name: grader
description: >-
  Scores software artifacts across dimensions and produces a graded report with
  strengths, weaknesses, and prioritized fixes. Use when the user mentions
  grader, 打分, 评分, scorecard, 项目体检, audit UI, 评架构, 代码质量评估, 优缺点,
  grade my UI, score backend architecture, or asks for a multi-dimension
  quality score on frontend UI, backend architecture, backend quality,
  frontend code, API design, security, database, testing, or devops.
license: MIT
metadata:
  version: "1.0.0"
  author: mskill
---

# Grader

按类型对开发产物多维度打分，输出总分、分项分、优点、缺点与可执行改进建议。

## 工作流

复制并跟踪：

```
Grader Progress:
- [ ] 1. 确定类型与范围
- [ ] 2. 加载对应评分卡
- [ ] 3. 收集证据（读文件/结构）
- [ ] 4. 按维度 0–10 打分并加权
- [ ] 5. 输出报告（Markdown + YAML）
```

### 1. 确定类型与范围

从用户意图或路径推断类型 ID。无法判断时，先问一句再继续。

| 类型 ID | 何时使用 | 评分卡 |
|---------|----------|--------|
| `frontend-ui` | 页面/视觉/UX/落地页设计 | [frontend-ui.md](references/frontend-ui.md) |
| `backend-architecture` | 分层、模块边界、系统结构 | [backend-architecture.md](references/backend-architecture.md) |
| `backend-quality` | 后端实现质量、可维护性 | [backend-quality.md](references/backend-quality.md) |
| `frontend-code` | 前端组件/状态/实现质量 | [frontend-code.md](references/frontend-code.md) |
| `api-design` | HTTP/RPC 契约与 API 形态 | [api-design.md](references/api-design.md) |
| `security` | 安全风险与防护 | [security.md](references/security.md) |
| `database` | 模型、查询、迁移 | [database.md](references/database.md) |
| `testing` | 测试策略与用例质量 | [testing.md](references/testing.md) |
| `devops` | CI/CD、发布、配置 | [devops.md](references/devops.md) |

范围：用户指定的路径/文件；未指定则评与类型相关的核心目录，并在报告中写明范围。

全面体检：按仓库内容选 2–4 个最相关类型分别打分，再给一段综合总评（不虚构未评类型的分数）。

### 2. 加载评分卡

只读取当前类型对应的 `references/*.md`，以及 [report-template.md](references/report-template.md)。不要一次加载全部评分卡。

### 3. 收集证据

- 阅读相关源码、样式、配置、目录结构
- 每个维度的分数必须能指向具体文件/符号/模式
- 信息不足时该维标 `N/A`，说明假设；禁止假装评过

### 4. 打分规则

- 每维度：**0–10**（整数或一位小数）
- 使用评分卡中的权重计算加权平均，再映射到 **0–100** 总分：
  `total = round(100 * Σ(score_i * weight_i) / Σ(weight_i))`（仅计入非 N/A 维度；权重按剩余维归一）
- 等级：`S` ≥90 · `A` ≥80 · `B` ≥70 · `C` ≥60 · `D` <60
- 锚点：0–3 差 · 4–6 中 · 7–8 良 · 9–10 优（以各评分卡细则为准）
- 禁止空泛打分；禁止所有维度同分凑数

### 5. 输出报告

严格按 [report-template.md](references/report-template.md) 输出：

1. Markdown 报告（总评 → 分数表 → 优点 → 缺点 → 改进清单）
2. YAML `scorecard` 块

改进建议分 **P0 / P1 / P2**，每条写清：改什么、为何、预期提分维度。

## 原则

- 证据优先，意见其次
- 对标该类型评分卡，不混用其他类型维度
- 语气直接、可执行；不吹捧、不恐吓
- 工具无关：只依赖本 skill 的 markdown，不调用专有评分 API
