# Rubric · devops

**Category:** `ops`  
CI/CD, environments, release, config, supply chain.

## Dimensions & weights

| ID | Dimension | Weight | Sub-criteria |
|----|-----------|--------|--------------|
| `ci` | Continuous integration | 16 | `pr_checks`, `gating`, `feedback_speed` |
| `cd_release` | Release & deploy | 14 | `repeatability`, `promotion`, `approvals` |
| `rollback` | Rollback | 14 | `artifact_rollback`, `migration_compat`, `flags` |
| `config_secrets` | Config & secrets | 16 | `separation`, `secret_injection`, `boot_validation` |
| `environments` | Environment parity | 12 | `env_set`, `drift_control`, `iac` |
| `observability_ops` | Runtime observability | 14 | `health`, `alerts`, `log_ship` |
| `supply_chain` | Build supply chain | 14 | `lock_pin`, `image_provenance`, `ci_least_privilege` |

Weights sum to 100.

## Evidence checklist

Workflows, Docker/deploy/IaC, env samples, health/alerts, branch protection hints. Cloud IAM → `N/A` if invisible.

## Sub-criteria

| Dimension | Subs |
|-----------|------|
| `ci` | Build+test+lint on PRs; failures block; useful speed/cache |
| `cd_release` | Repeatable deploys; env promotion; sensible gates |
| `rollback` | Prior artifact restore; compatible migrations; feature flags |
| `config_secrets` | Config≠code; secrets via env/manager; config validated at boot |
| `environments` | Dev/stage/prod exist; drift controlled; IaC or equivalent |
| `observability_ops` | Health/ready; alerting; centralized logs |
| `supply_chain` | Lockfiles; trusted bases; least-privilege CI identities |

Build-without-test CI → mid/low `ci`. Ungated push-to-prod → low `cd_release`/`rollback`.
