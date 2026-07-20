# Rubric · database

**Category:** `data`  
Schema, queries, transactions, migrations. NoSQL: map schema/indexing to collections & access patterns.

## Dimensions & weights

| ID | Dimension | Weight | Sub-criteria |
|----|-----------|--------|--------------|
| `schema` | Schema design | 16 | `modeling`, `constraints`, `relationship_clarity` |
| `indexing` | Indexing | 14 | `hot_path_indexes`, `write_cost`, `over_index_risk` |
| `queries` | Query quality | 16 | `n_plus_one`, `bounded_reads`, `select_discipline` |
| `transactions` | Transactions | 14 | `boundaries`, `isolation_awareness`, `partial_failure` |
| `migrations` | Migrations | 14 | `reproducible`, `expand_contract`, `backfill_safety` |
| `integrity` | Integrity | 12 | `uniqueness`, `nullability`, `db_vs_app_rules` |
| `ops` | Operational readiness | 14 | `pooling`, `slow_query_visibility`, `ddl_risk` |

Weights sum to 100.

## Evidence checklist

Migrations/DDL, repositories/DAOs, indexes, multi-step writes, pool settings.

## Sub-criteria

| Dimension | Subs |
|-----------|------|
| `schema` | Fit normalization; FKs/enums; clear entities |
| `indexing` | Hot filters/FKs indexed; write overhead considered; no index spam |
| `queries` | No clear N+1; lists paginated; avoid select-* abuse |
| `transactions` | Correct multi-write boundaries; contention considered |
| `migrations` | Repeatable history; safe expand/contract; locked-table caution |
| `integrity` | Uniqueness/null/checks in DB where needed |
| `ops` | Pool discipline; slow-query observability; large DDL risk managed |

Without prod metrics, label perf claims as **risk**, not incidents.
