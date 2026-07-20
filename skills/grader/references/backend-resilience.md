# Rubric · backend-resilience

**Category:** `backend`  
Score **failure handling, degradation, and observability design**.  
Module shape → `backend-architecture`. Line-level quality → `backend-quality`.

## Dimensions & weights

| ID | Dimension | Weight | Sub-criteria |
|----|-----------|--------|--------------|
| `timeouts` | Timeouts & deadlines | 16 | `outbound_deadlines`, `inbound_limits`, `propagation` |
| `retries` | Retries & backoff | 14 | `retry_policy`, `idempotent_retries`, `jitter` |
| `isolation` | Isolation & bulkheads | 14 | `dependency_isolation`, `queue_isolation`, `resource_limits` |
| `degradation` | Degradation & fallback | 14 | `fallback_paths`, `feature_shed`, `default_safe` |
| `idempotency` | Idempotency | 14 | `write_idempotency`, `dedupe_store`, `at_least_once_safe` |
| `observability` | Observability | 16 | `correlation`, `structured_logs`, `metrics_traces` |
| `readiness` | Health & readiness | 12 | `liveness_readiness`, `dependency_probes`, `drain` |

Weights sum to 100.

## Evidence checklist

- HTTP/gRPC clients: timeouts, retries
- Circuit breakers / bulkheads / concurrency limits
- Consumer/worker ack/retry/DLQ patterns
- Idempotency keys; outbox/inbox
- Logging/tracing middleware; metrics
- `/health` `/ready` (or equivalents)

## Sub-criteria

### timeouts
| Sub | Inspect |
|-----|---------|
| `outbound_deadlines` | External calls bounded |
| `inbound_limits` | Server/request timeouts sensible |
| `propagation` | Deadlines passed downstream when applicable |

### retries
| Sub | Inspect |
|-----|---------|
| `retry_policy` | Explicit max/backoff—not infinite loops |
| `idempotent_retries` | Only safe operations auto-retried |
| `jitter` | Avoid thundering herds |

### isolation
| Sub | Inspect |
|-----|---------|
| `dependency_isolation` | One bad dep doesn’t wedge all traffic |
| `queue_isolation` | Separate critical vs bulk workloads |
| `resource_limits` | Pool sizes, rate limits, memory guards |

### degradation
| Sub | Inspect |
|-----|---------|
| `fallback_paths` | Cached/default responses when justified |
| `feature_shed` | Shed non-critical work under load |
| `default_safe` | Fail closed on auth/payments; fail soft on optional enrichments |

### idempotency
| Sub | Inspect |
|-----|---------|
| `write_idempotency` | Create/payment endpoints safe to retry |
| `dedupe_store` | Key/store or equivalent |
| `at_least_once_safe` | Consumers tolerate duplicates |

### observability
| Sub | Inspect |
|-----|---------|
| `correlation` | Request/trace IDs |
| `structured_logs` | Queryable fields; useful levels |
| `metrics_traces` | RED/USE or spans on critical paths |

### readiness
| Sub | Inspect |
|-----|---------|
| `liveness_readiness` | Distinct probes when needed |
| `dependency_probes` | Ready reflects critical deps honestly |
| `drain` | Graceful shutdown / in-flight handling

## Scoring notes

- No timeout on payment/DB paths → `outbound_deadlines` ≤3, likely P0
- Don’t double-count pure layering issues—send those to `backend-architecture`
