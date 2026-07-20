# Grader

Open-source **Agent Skill** for fine-grained scoring of software artifacts.

Hierarchy: **category → type → dimension → sub-criterion** → weighted total, strengths/weaknesses, P0–P2 fixes.

符合 [Agent Skills](https://agentskills.io/specification) 开放标准（Cursor / Claude Code / Codex 等）。

- **Rubrics / `SKILL.md`:** English  
- **Report template:** Chinese structure; prose follows the user language  

## Score types

| Category | Type ID | Focus |
|----------|---------|--------|
| `frontend` | `frontend-ui` | Visual design, brand, **UI creativity** |
| `frontend` | `frontend-ux` | Flows, IA, responsive, **user acceptance** |
| `frontend` | `frontend-motion` | Motion, **micro-animations**, motion acceptability |
| `frontend` | `frontend-a11y` | Accessibility deep-dive |
| `frontend` | `frontend-code` | Components, state, types, FE structure |
| `frontend` | `frontend-performance` | Rendering, bundle, data/perf hygiene |
| `backend` | `backend-architecture` | Boundaries, layering, cohesion, fit |
| `backend` | `backend-quality` | Correctness, errors, complexity, BE tests |
| `backend` | `backend-resilience` | Timeouts, retries, degradation, observability |
| `backend` | `api-design` | Contracts, errors, versioning, idempotency |
| `security` | `security` | Authn/z, injection, secrets, sensitive data |
| `data` | `database` | Schema, indexes, queries, migrations |
| `quality` | `testing` | Strategy, assertions, isolation, feedback |
| `ops` | `devops` | CI/CD, rollback, config, supply chain |

Each dimension is scored from **sub-criteria** (average), then weighted into a **0–100** total.

## Install

Copy `skills/grader` into your tool’s skills path (keep folder name `grader`):

| Tool | Path |
|------|------|
| Cursor | `~/.cursor/skills/grader/` or `.cursor/skills/grader/` |
| Claude Code | `~/.claude/skills/grader/` or `.claude/skills/grader/` |
| Codex | `~/.agents/skills/grader/` or `.agents/skills/grader/` |

```bash
git clone https://github.com/wei63w/grader-skill.git
cp -r grader-skill/skills/grader ~/.cursor/skills/grader
```

```powershell
git clone https://github.com/wei63w/grader-skill.git
Copy-Item -Recurse grader-skill\skills\grader $HOME\.cursor\skills\grader
```

## Usage

- `Score this landing page UI with grader` → `frontend-ui`
- `grader 评交互、信息架构和用户接受度` → `frontend-ux`
- `grader 评动效和微动画` → `frontend-motion`
- `grader 评 UI 创意` → `frontend-ui` (`ui_creativity`)
- `grader a11y audit`
- `Score backend resilience`
- `用 grader 做项目体检` → multi-type (one per relevant category)

## Output

1. Markdown report: summary → **dimension table** → **sub-score tables** → strengths/weaknesses → P0/P1/P2  
2. YAML `scorecard` with nested `dimensions.*.subs`

Grades: `S` ≥90 · `A` ≥80 · `B` ≥70 · `C` ≥60 · `D` <60

## Layout

```
skills/grader/
├── SKILL.md
└── references/
    ├── report-template.md
    ├── frontend-ui.md
    ├── frontend-ux.md
    ├── frontend-motion.md
    ├── frontend-a11y.md
    ├── frontend-code.md
    ├── frontend-performance.md
    ├── backend-architecture.md
    ├── backend-quality.md
    ├── backend-resilience.md
    ├── api-design.md
    ├── security.md
    ├── database.md
    ├── testing.md
    └── devops.md
```

## License

MIT — see [LICENSE](LICENSE)
