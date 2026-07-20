# Rubric · backend-quality

**Category:** `backend`  
Implementation quality. Architecture → `backend-architecture`. Security exploits → `security`. Resilience policies → `backend-resilience`.

## Dimensions & weights

| ID | Dimension | Weight | Sub-criteria |
|----|-----------|--------|--------------|
| `correctness` | Correctness & edges | 20 | `happy_path`, `edge_cases`, `invariants` |
| `error_handling` | Error handling | 16 | `classification`, `propagation`, `client_safety` |
| `naming_structure` | Naming & structure | 12 | `names`, `function_size`, `abstraction_level` |
| `complexity` | Duplication & complexity | 14 | `duplication`, `nesting`, `separations` |
| `testing` | Test adequacy | 14 | `critical_coverage`, `assertion_strength`, `regression_value` |
| `concurrency` | Concurrency & resources | 12 | `shared_state`, `lifecycle`, `race_risk` |
| `diagnostics` | Diagnostics | 6 | `log_context`, `actionability` |
| `consistency` | Style consistency | 6 | `idioms`, `error_model_unity` |

Weights sum to 100.

## Evidence checklist

Sample ≥2 vertical slices (handler → domain → persistence); tests; logging; shared mutable state.

## Sub-criteria

| Dimension | Subs |
|-----------|------|
| `correctness` | Main behavior correct; null/empty/limits handled; invariants held on failure too |
| `error_handling` | Typed/classified errors; wrap/map sane; no secret leaks / swallowed catches |
| `naming_structure` | Intention-revealing names; focused functions; stable layers of abstraction |
| `complexity` | Controlled copy-paste; shallow control flow; I/O≠policy≠formatting mixed less |
| `testing` | Critical paths tested; assertions meaningful; suite would catch regressions |
| `concurrency` | Shared state disciplined; pools/files closed; races considered |
| `diagnostics` | Contextual logs; failures locatable |
| `consistency` | Project patterns applied evenly |

**Honest rule:** near-zero tests ⇒ low `testing` (+ P0/P1).

## Overlap

| Issue | Prefer |
|-------|--------|
| Logic in controllers | `backend-architecture` |
| SQL injection | `security` |
| Missing outbound timeouts | `backend-resilience` |
