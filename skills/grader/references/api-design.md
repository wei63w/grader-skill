# Rubric · api-design

**Category:** `backend`  
API/contract design. Implementation → `backend-quality`. Exploitability → `security`.

## Dimensions & weights

| ID | Dimension | Weight | Sub-criteria |
|----|-----------|--------|--------------|
| `resource_model` | Resource/model clarity | 14 | `nouns`, `boundaries`, `graph_fit` |
| `naming` | Naming & style | 12 | `paths`, `fields`, `conventions` |
| `contracts` | Request/response contracts | 14 | `schema`, `required_optional`, `examples` |
| `errors` | Error model | 14 | `shape`, `codes`, `actionability` |
| `versioning` | Versioning & compatibility | 10 | `strategy`, `breaking_policy`, `deprecation` |
| `idempotency` | Idempotency & safety | 12 | `safe_methods`, `write_keys`, `retry_semantics` |
| `pagination_filter` | Lists & filtering | 12 | `pagination`, `sort`, `filter_grammar` |
| `authz_surface` | Auth surface | 12 | `scheme_clarity`, `per_route`, `least_privilege` |

Weights sum to 100.

## Evidence checklist

OpenAPI/proto/GraphQL schema, route tables, error middleware, auth requirements, list params, idempotency headers.

## Sub-criteria

| Dimension | Subs |
|-----------|------|
| `resource_model` | Consistent nouns; clear resource edges; GraphQL type-graph clarity |
| `naming` | Predictable paths/fields; plural rules; one style |
| `contracts` | Explicit schemas; required/optional clear; examples match reality |
| `errors` | Stable envelope; meaningful codes; actionable, non-leaky |
| `versioning` | Documented strategy; breaking-change rules; deprecation path |
| `idempotency` | Safe GETs; critical writes idempotent; retry semantics documented |
| `pagination_filter` | One list style; stable sort; documented filters |
| `authz_surface` | Auth scheme clear; per-operation requirements; least privilege expressible |

**Note:** Always-200 + business code can score well if consistent and documented.
