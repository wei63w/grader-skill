# Grader

开源 Agent Skill：按类型对开发产物多维度打分，输出总分、分项分、优点、缺点与可执行改进建议。

Open-source Agent Skill for multi-dimension scoring of frontend UI, backend architecture, code quality, and more.

符合 [Agent Skills](https://agentskills.io/specification) 开放标准，可用于 Cursor、Claude Code、Codex 等任意支持该标准的 AI 工具。

## 评分类型 / Score Types

| ID | 说明 |
|----|------|
| `frontend-ui` | 页面视觉、层级、间距、品牌、交互、响应式、无障碍 |
| `backend-architecture` | 分层、边界、依赖方向、扩展性、一致性、可观测性 |
| `backend-quality` | 正确性、错误处理、可读性、测试、复杂度、一致性 |
| `frontend-code` | 组件结构、状态、性能、可维护性 |
| `api-design` | REST/RPC 契约、命名、版本、错误模型、幂等 |
| `security` | 认证授权、注入、密钥、输入校验、敏感数据 |
| `database` | 模型、索引、事务、迁移、查询效率 |
| `testing` | 覆盖策略、断言质量、可测性、脆弱测试 |
| `devops` | CI/CD、环境、可回滚、配置与密钥管理 |

## 安装 / Install

将 `skills/grader` 目录复制到工具的 skills 路径（目录名保持 `grader`）：

| 工具 | 路径 |
|------|------|
| Cursor | `~/.cursor/skills/grader/` 或项目内 `.cursor/skills/grader/` |
| Claude Code | `~/.claude/skills/grader/` 或项目内 `.claude/skills/grader/` |
| Codex | `~/.agents/skills/grader/` 或项目内 `.agents/skills/grader/` |
| 通用 | 复制到该工具文档中的 skills 目录 |

```bash
# 示例：克隆后安装到 Cursor（个人）
git clone https://github.com/wei63w/grader.git
cp -r grader/skills/grader ~/.cursor/skills/grader
```

Windows PowerShell:

```powershell
git clone https://github.com/wei63w/grader.git
Copy-Item -Recurse grader\skills\grader $HOME\.cursor\skills\grader
```

## 用法 / Usage

在对话中直接说：

- 「用 grader 评这个前端页面」
- 「grader 给后端架构打分」
- 「用 grader 做项目体检」
- 「Score this UI with grader」
- 「/grader」

未指定类型时，agent 会根据路径/技术栈推断，或先确认评测类型。

## 输出 / Output

每次评测同时给出：

1. **Markdown 报告**：总评 → 分数表 → 优点 → 缺点 → P0/P1/P2 改进清单
2. **YAML 分数块**：便于存档或二次处理

### 评分规则 / Scoring

- 每维度 **0–10**（须引用文件/符号等证据；禁止空泛打分）
- 按评分卡权重加权，映射为总分 **0–100**
- 等级：`S` ≥90 · `A` ≥80 · `B` ≥70 · `C` ≥60 · `D` <60
- 信息不足标 `N/A`，并说明假设

### 报告示例片段

```yaml
scorecard:
  skill: grader
  type: frontend-ui
  total: 78
  grade: B
  dimensions:
    visual_hierarchy:
      score: 8
      weight: 12
      note: "Hero headline dominates; secondary CTAs quieter"
```

## 仓库结构 / Structure

```
skills/grader/
├── SKILL.md
└── references/
    ├── frontend-ui.md
    ├── backend-architecture.md
    ├── backend-quality.md
    ├── frontend-code.md
    ├── api-design.md
    ├── security.md
    ├── database.md
    ├── testing.md
    ├── devops.md
    └── report-template.md
```

## License

MIT — 见 [LICENSE](LICENSE)
