# 评分卡 · frontend-code

前端实现质量打分（组件、状态、性能、可维护性）。视觉与 UX 用 `frontend-ui`。

## 权重与维度

| ID | 维度 | 权重 | 看什么 |
|----|------|------|--------|
| `component_structure` | 组件结构 | 15 | 拆分是否合理；容器/展示职责；prop 膨胀 |
| `state_management` | 状态管理 | 15 | 状态放哪一层；派生 vs 重复状态；副作用边界 |
| `data_fetching` | 数据获取 | 12 | 缓存、加载/错误态、竞态、与 UI 解耦 |
| `performance` | 性能 | 12 | 不必要重渲染、大列表、包体积、关键路径卡顿风险 |
| `types_contracts` | 类型与契约 | 12 | TS/PropTypes 质量；API 类型是否漂移 |
| `reusability` | 复用与抽象 | 10 | 有意义复用；有无过早/错误抽象 |
| `testability` | 可测性 | 12 | 是否可测；关键逻辑是否有测 |
| `consistency` | 一致性 | 12 | 项目模式、目录、命名、错误处理是否统一 |

权重合计 100。

## 打分锚点（摘要）

- **0–3**：结构混乱、状态到处都是、无类型/无测、明显性能陷阱
- **4–6**：能跑，气味多，模式不统一
- **7–8**：结构清楚，状态与数据流合理，关键处有保护
- **9–10**：抽象恰当，性能与可测性有意设计，一致性高

### 分维提示
- `component_structure`：过大组件、深层 prop drilling 降分
- `state_management`：服务器状态当本地状态、重复 source of truth 降分
- `performance`：无虚拟列表的大表、无防抖的昂贵计算、滥加 memo 都不加分
- `types_contracts`：`any` 泛滥、断言瞒过编译器降分

## 评测时注意

- 抽查路由页、共享组件、数据层；不要只评 `utils`
- React Compiler / 团队已有 memo 规范时，按其规范评，不强制加 `useMemo`
