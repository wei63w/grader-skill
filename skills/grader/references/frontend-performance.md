# Rubric · frontend-performance

**Category:** `frontend`  
Score **runtime performance, rendering cost, and bundle/delivery**. Structure/state quality → `frontend-code`.

## Dimensions & weights

| ID | Dimension | Weight | Sub-criteria |
|----|-----------|--------|--------------|
| `rendering` | Rendering efficiency | 20 | `update_cost`, `list_strategy`, `layout_thrash` |
| `startup` | Startup & route cost | 18 | `bundle_split`, `critical_path`, `hydration_cost` |
| `assets` | Assets & media | 14 | `image_strategy`, `font_strategy`, `cache_headers_guess` |
| `data_perf` | Data fetching perf | 16 | `overfetch`, `waterfall`, `cache_reuse` |
| `main_thread` | Main-thread hygiene | 16 | `long_tasks`, `debounce_throttle`, `worker_offload` |
| `perf_tooling` | Perf awareness | 16 | `measure_hooks`, `budgets`, `regression_guards` |

Weights sum to 100.

## Evidence checklist

- Route entry imports; dynamic `import()` / lazy boundaries
- Large lists/tables; virtualization
- Image/`next/image`/srcset usage; font loading
- Fetch waterfalls in page trees; cache libraries
- Perf budgets in CI / Lighthouse configs if any

Without profiling, score as **risk from code structure** and say so.

## Sub-criteria

### rendering
| Sub | Inspect |
|-----|---------|
| `update_cost` | Broad contexts causing mass re-render; unstable props |
| `list_strategy` | Virtualize long lists; stable keys |
| `layout_thrash` | Avoid read/write layout loops; heavy sync work in render |

Do **not** reward cargo-cult `useMemo`—only evidenced wins or Compiler-aligned code.

### startup
| Sub | Inspect |
|-----|---------|
| `bundle_split` | Heavy deps not on first paint path |
| `critical_path` | Above-the-fold JS/CSS minimal |
| `hydration_cost` | Excess client JS on static pages |

### assets
| Sub | Inspect |
|-----|---------|
| `image_strategy` | Right size/format; lazy below fold |
| `font_strategy` | Subset/display swap; avoid FOIT disasters |
| `cache_headers_guess` | Build emits hashable static assets (N/A if unknown)

### data_perf
| Sub | Inspect |
|-----|---------|
| `overfetch` | Payloads trimmed to need |
| `waterfall` | Parallelize independent requests |
| `cache_reuse` | Shared cache keys / dedupe

### main_thread
| Sub | Inspect |
|-----|---------|
| `long_tasks` | Heavy CPU in handlers/render |
| `debounce_throttle` | Input/scroll handlers tamed |
| `worker_offload` | CPU-heavy work off main thread when justified |

### perf_tooling
| Sub | Inspect |
|-----|---------|
| `measure_hooks` | RUM/analytics or profiling hooks exist |
| `budgets` | Bundle/Lighthouse budgets |
| `regression_guards` | CI or docs preventing silent regressions |

## Scoring notes

- Cite concrete modules (e.g. imported chart lib on landing)
- Cross-link UX jank perception to `frontend-ux` only if scoring both
