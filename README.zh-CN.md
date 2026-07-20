# Grader

[English](./README.md) | **中文**

[![skills.sh](https://skills.sh/b/wei63w/grader-skill)](https://skills.sh/wei63w/grader-skill)

面向软件产物的 Agent Skill：给 UI、动效、架构、质量、安全等做多维打分。

Agent 很能写，但不一定校准得好。你要「好看的 UI」或「扎实的后端」，经常得到自信的空话、偏软的分数，以及缺少证据的评价。

Grader 给 Agent 一套严格评分卡：**类别 → 类型 → 维度 → 子项**，带证据的 0–10 分、0–100 总分，以及 P0/P1/P2 改进项。评分卡正文为英文；报告模板为中文结构，叙述语言跟随用户。

兼容 [Agent Skills](https://agentskills.io/specification) 开放标准（Cursor、Claude Code、Codex 等）。

## 安装

```bash
npx skills@latest add wei63w/grader-skill
```

或将 `skills/grader` 复制到工具的 skills 目录：

| 工具 | 路径 |
|------|------|
| Cursor | `~/.cursor/skills/grader/` |
| Claude Code | `~/.claude/skills/grader/` |
| Codex | `~/.agents/skills/grader/` |

```bash
git clone https://github.com/wei63w/grader-skill.git
cp -r grader-skill/skills/grader ~/.cursor/skills/grader
```

## 为什么用它？

Agent 的打分不稳定。

没有统一评分卡时，同一张落地页周一是「挺精致」，周二又变成「还不行」。视觉层级、动效克制、对象级授权、迁移风险，全被揉成「感觉」。

Grader 把各场景真正会翻车的点列出来——AI 套版审美、吵闹的微动画、缺失的对象级鉴权、测不到的热路径——并要求 Agent 引用文件、给子项打分、排出修复优先级。

这是一份能动手改的审查，不是又一堵夸奖墙。

## 参考

入口 Skill：

- **[grader](./skills/grader/SKILL.md)** — 路由到对应评分卡，按子项 → 维度 → 总分计分，经 [report-template.md](./skills/grader/references/report-template.md) 输出 Markdown + YAML。

### 前端

- **[frontend-ui](./skills/grader/references/frontend-ui.md)** — 视觉层级、字体、间距、色彩、品牌、**UI 创意**。
- **[frontend-ux](./skills/grader/references/frontend-ux.md)** — 流程、信息架构、响应式、**用户接受度**。
- **[frontend-motion](./skills/grader/references/frontend-motion.md)** — 动效目的、**微动画**、时序、可接受度、reduced-motion。
- **[frontend-mobile](./skills/grader/references/frontend-mobile.md)** — **移动端/App**：安全区、触控手势、导航、平台惯例、弱网离线。
- **[frontend-a11y](./skills/grader/references/frontend-a11y.md)** — 语义、键盘、标签、对比度、辅助技术。
- **[frontend-code](./skills/grader/references/frontend-code.md)** — 组件、状态、类型、结构。
- **[frontend-performance](./skills/grader/references/frontend-performance.md)** — 渲染成本、包体/启动、数据请求性能。

### 后端与平台

- **[backend-architecture](./skills/grader/references/backend-architecture.md)** — 边界、分层、内聚、问题匹配度。
- **[backend-quality](./skills/grader/references/backend-quality.md)** — 正确性、错误处理、复杂度、测试。
- **[backend-resilience](./skills/grader/references/backend-resilience.md)** — 超时、重试、降级、可观测性。
- **[api-design](./skills/grader/references/api-design.md)** — 契约、错误模型、版本、幂等。
- **[security](./skills/grader/references/security.md)** — 认证授权、注入、密钥、敏感数据。
- **[database](./skills/grader/references/database.md)** — 模型、索引、查询、迁移。
- **[testing](./skills/grader/references/testing.md)** — 策略、断言、隔离、反馈速度。
- **[devops](./skills/grader/references/devops.md)** — CI/CD、回滚、配置、供应链。

## 怎么打分

1. 选定类型（或由 Agent 推断；全面体检时每个相关类别选一种类型）。
2. 每个**子项** 0–10 分并附证据（不足则 `N/A`）。
3. 维度分 = 子项平均；总分 = 维度加权 → **0–100**。
4. 等级：`S` ≥90 · `A` ≥80 · `B` ≥70 · `C` ≥60 · `D` <60。
5. 报告：总评 → 维度表 → 子项表 → 优缺点 → P0/P1/P2 + YAML `scorecard`。

动效更多、花样更新，不等于分更高。目的、克制、契合度优先于装饰。

## 示例

```
> Score this landing page UI with grader
> grader 评交互、信息架构和用户接受度
> grader 评动效和微动画
> grader 评这个 iOS/Android App / 移动端体验
> grader 评 UI 创意
> Score backend resilience with grader
> 用 grader 做项目体检
```

窄问题会落到细类型（`frontend-motion`、`frontend-mobile`、`frontend-a11y` 等）。宽泛的「这个页面怎么样？」常会跑 `frontend-ui` + `frontend-ux` + `frontend-motion`。宽泛的「这个 App 怎么样？」通常加上 `frontend-mobile`。

## License

MIT — 见 [LICENSE](LICENSE)
