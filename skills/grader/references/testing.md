# Rubric · testing

**Category:** `quality`  
Test strategy and case quality—not coverage % alone.

## Dimensions & weights

| ID | Dimension | Weight | Sub-criteria |
|----|-----------|--------|--------------|
| `strategy` | Strategy & pyramid | 14 | `layer_balance`, `guidance`, `right_tool` |
| `critical_paths` | Critical-path coverage | 18 | `core_flows`, `money_auth_data`, `edge_risks` |
| `assertion_quality` | Assertion quality | 16 | `behavior_focus`, `oracle_strength`, `snapshot_discipline` |
| `isolation` | Isolation & stability | 14 | `determinism`, `no_order_deps`, `network_control` |
| `testdata` | Test data | 10 | `factories`, `minimal_data`, `no_shared_mut` |
| `speed_feedback` | Speed & feedback | 10 | `unit_speed`, `ci_staging`, `local_loop` |
| `bug_prevention` | Bug-prevention power | 18 | `regression_net`, `real_failure_modes`, `refactor_safety` |

Weights sum to 100.

## Evidence checklist

Runner config, sample unit/integration/E2E, CI test jobs, snapshot volume. If not executed, state **not executed**.

## Sub-criteria

| Dimension | Subs |
|-----------|------|
| `strategy` | Sensible unit/integration/E2E mix; documented norms |
| `critical_paths` | Core journeys covered; auth/payment/data-loss paths prioritized |
| `assertion_quality` | Assert behavior; strong oracles; snapshots reviewed/rare |
| `isolation` | Deterministic; no order dependence; controlled time/network |
| `testdata` | Clear factories; minimal fixtures; no leaky globals |
| `speed_feedback` | Fast unit layer; CI not only giant E2E |
| `bug_prevention` | Would catch real regressions; not decorative |

High coverage + weak assertions ≠ high score.
