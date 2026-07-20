# Grader

**English** | [中文](./README.zh-CN.md)

[![skills.sh](https://skills.sh/b/wei63w/grader-skill)](https://skills.sh/wei63w/grader-skill)

An Agent Skill for scoring software — UI, motion, architecture, quality, security, and more.

Agents are fluent. They are not always calibrated. Ask for a “good UI” or a “solid backend” and you often get confident prose with soft scores and no evidence.

Grader gives the agent a strict rubric: **category → type → dimension → sub-criterion**, evidence-backed 0–10 scores, a 0–100 total, and P0/P1/P2 fixes. Rubrics are English. The report template is Chinese-structured; written prose follows the user’s language.

Compatible with the [Agent Skills](https://agentskills.io/specification) open standard (Cursor, Claude Code, Codex, and others).

## Install

```bash
npx skills@latest add wei63w/grader-skill
```

Or copy `skills/grader` into your tool’s skills directory:

| Tool | Path |
|------|------|
| Cursor | `~/.cursor/skills/grader/` |
| Claude Code | `~/.claude/skills/grader/` |
| Codex | `~/.agents/skills/grader/` |

```bash
git clone https://github.com/wei63w/grader-skill.git
cp -r grader-skill/skills/grader ~/.cursor/skills/grader
```

## Why use it?

Agents don’t grade consistently.

Without a shared scorecard, the same landing page can be “looks polished” on Monday and “needs work” on Tuesday. Hierarchy, motion restraint, authz gaps, and migration risk all get flattened into vibes.

Grader lists the failure modes that matter for each surface — AI-slop visuals, noisy micro-animations, missing object-level auth, untestable hot paths — and forces the agent to cite files, score sub-criteria, and prioritize fixes.

It’s a shortcut to a review you can act on. Not another wall of compliments.

## Reference

The entry skill:

- **[grader](./skills/grader/SKILL.md)** — Routes to the right rubric, scores sub-criteria → dimensions → total, emits Markdown + YAML via [report-template.md](./skills/grader/references/report-template.md).

### Frontend

- **[frontend-ui](./skills/grader/references/frontend-ui.md)** — Visual hierarchy, type, space, color, brand, **UI creativity**.
- **[frontend-ux](./skills/grader/references/frontend-ux.md)** — Flows, IA, responsive behavior, **user acceptance**.
- **[frontend-motion](./skills/grader/references/frontend-motion.md)** — Motion purpose, **micro-animations**, timing, acceptability, reduced-motion.
- **[frontend-mobile](./skills/grader/references/frontend-mobile.md)** — **Mobile/app**: safe areas, touch/gestures, navigation, platform conventions, offline.
- **[frontend-a11y](./skills/grader/references/frontend-a11y.md)** — Semantics, keyboard, labels, contrast, assistive tech.
- **[frontend-code](./skills/grader/references/frontend-code.md)** — Components, state, types, structure.
- **[frontend-performance](./skills/grader/references/frontend-performance.md)** — Rendering cost, bundle/startup, data-fetch perf.

### Backend & platform

- **[backend-architecture](./skills/grader/references/backend-architecture.md)** — Boundaries, layering, cohesion, fit.
- **[backend-quality](./skills/grader/references/backend-quality.md)** — Correctness, errors, complexity, tests.
- **[backend-resilience](./skills/grader/references/backend-resilience.md)** — Timeouts, retries, degradation, observability.
- **[api-design](./skills/grader/references/api-design.md)** — Contracts, errors, versioning, idempotency.
- **[security](./skills/grader/references/security.md)** — Authn/z, injection, secrets, sensitive data.
- **[database](./skills/grader/references/database.md)** — Schema, indexes, queries, migrations.
- **[testing](./skills/grader/references/testing.md)** — Strategy, assertions, isolation, feedback.
- **[devops](./skills/grader/references/devops.md)** — CI/CD, rollback, config, supply chain.

## How scoring works

1. Pick a type (or let the agent infer; for a full checkup, one type per relevant category).
2. Score every **sub-criterion** 0–10 with evidence (or `N/A`).
3. Dimension score = average of its subs. Total = weighted dimensions → **0–100**.
4. Grade: `S` ≥90 · `A` ≥80 · `B` ≥70 · `C` ≥60 · `D` <60.
5. Report: summary → dimension table → sub-score tables → strengths / weaknesses → P0/P1/P2 + YAML `scorecard`.

More motion or novelty is not automatically a higher score. Purpose, restraint, and fit beat decoration.

## Examples

```
> Score this landing page UI with grader
> grader 评交互、信息架构和用户接受度
> grader 评动效和微动画
> grader 评这个 iOS/Android App / 移动端体验
> grader 评 UI 创意
> Score backend resilience with grader
> 用 grader 做项目体检
```

Narrow prompts map to finer types (`frontend-motion`, `frontend-mobile`, `frontend-a11y`, …). Broad “how’s this page?” often runs `frontend-ui` + `frontend-ux` + `frontend-motion`. Broad “how’s this app?” often adds `frontend-mobile`.

## License

MIT — see [LICENSE](LICENSE)
