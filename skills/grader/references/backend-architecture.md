# Rubric · backend-architecture

**Category:** `backend`  
Score **structure & boundaries**. Resilience/telemetry design depth → `backend-resilience`. Line quality → `backend-quality`.

## Dimensions & weights

| ID | Dimension | Weight | Sub-criteria |
|----|-----------|--------|--------------|
| `boundaries` | Boundary clarity | 18 | `duty_clarity`, `domain_infra_split`, `crossing_discipline` |
| `layering` | Layering & deps | 18 | `direction`, `cycles`, `seam_testability` |
| `cohesion` | Module cohesion | 16 | `colocation`, `change_locality`, `god_module_risk` |
| `extensibility` | Extension points | 16 | `right_seams`, `no_switchyard`, `abstraction_rent` |
| `data_flow` | Data-flow consistency | 16 | `traceability`, `contract_stability`, `boundary_mapping` |
| `fit` | Problem fit | 16 | `complexity_match`, `team_match`, `growth_headroom` |

Weights sum to 100.

## Evidence checklist

Package map, entrypoints, import directions, adapters vs domain, ADRs/docs if any.

## Sub-criteria

### boundaries
| Sub | Inspect |
|-----|---------|
| `duty_clarity` | One-sentence module duties |
| `domain_infra_split` | Business rules not trapped in SQL/HTTP |
| `crossing_discipline` | Crossings via explicit adapters |

### layering
| Sub | Inspect |
|-----|---------|
| `direction` | Depend inward/on ports correctly |
| `cycles` | No package cycles |
| `seam_testability` | Critical seams replaceable in tests |

### cohesion
| Sub | Inspect |
|-----|---------|
| `colocation` | Related behavior together |
| `change_locality` | Features don’t shotgun the tree |
| `god_module_risk` | No mega-services |

### extensibility
| Sub | Inspect |
|-----|---------|
| `right_seams` | Strategy/ports where needed |
| `no_switchyard` | New features don’t edit one central monster |
| `abstraction_rent` | Abstractions pay for themselves |

### data_flow
| Sub | Inspect |
|-----|---------|
| `traceability` | Follow one write end-to-end |
| `contract_stability` | DTOs/events coherent |
| `boundary_mapping` | Explicit translations at edges |

### fit
| Sub | Inspect |
|-----|---------|
| `complexity_match` | Not under/over-designed |
| `team_match` | Ops/cognitive load fits team |
| `growth_headroom` | Structure survives near-term growth |

**Rule:** microservices ≠ automatic higher score than modular monolith.

Timeouts/retries/health → score in `backend-resilience` when that type is active (mention cross-link only if both run).
