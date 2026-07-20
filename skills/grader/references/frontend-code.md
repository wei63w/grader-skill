# Rubric · frontend-code

**Category:** `frontend`  
Score **component structure, state, types, reuse**—not visuals (`frontend-ui`) or deep perf (`frontend-performance`).

## Dimensions & weights

| ID | Dimension | Weight | Sub-criteria |
|----|-----------|--------|--------------|
| `component_structure` | Component structure | 18 | `split_quality`, `concern_separation`, `prop_surface` |
| `state_management` | State management | 18 | `ownership`, `single_source`, `effect_discipline` |
| `data_fetching` | Data fetching | 14 | `client_consistency`, `ui_decoupling`, `race_handling` |
| `types_contracts` | Types & contracts | 16 | `strictness`, `boundary_types`, `any_discipline` |
| `reusability` | Reuse & abstraction | 12 | `grain`, `api_quality`, `boolean_prop_trap` |
| `testability` | Testability | 12 | `pure_extract`, `critical_tests`, `hook_testability` |
| `consistency` | Consistency | 10 | `folder_patterns`, `naming`, `error_patterns` |

Weights sum to 100.

## Evidence checklist

Route pages, feature folders, stores/cache, API types, tests for non-trivial logic.

## Sub-criteria (summary)

| Dimension | Subs to verify |
|-----------|----------------|
| `component_structure` | Reasonable file size; container vs UI split; props not exploding |
| `state_management` | Server vs client ownership; no duplicated truth; effects not used as app logic dump |
| `data_fetching` | Shared client/library; fetch not buried randomly; abort/race handled |
| `types_contracts` | Strict TS where claimed; boundary schemas; low `any`/lie-casts |
| `reusability` | Right abstraction grain; clean component APIs; avoid boolean soup |
| `testability` | Logic testable outside JSX; critical paths have tests |
| `consistency` | Predictable project conventions |

**Anchors:** 0–3 chaotic · 4–6 works with smells · 7–8 solid · 9–10 intentional craft.

## Notes

Follow React Compiler / team memo norms—don’t require blanket `useMemo`. Perf issues → `frontend-performance`.
