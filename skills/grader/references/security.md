# Rubric · security

**Category:** `security`  
Security posture (read-only). Not a pentest. Confirmed high risk → **P0**. Never write exploit PoCs.

## Dimensions & weights

| ID | Dimension | Weight | Sub-criteria |
|----|-----------|--------|--------------|
| `authn` | Authentication | 14 | `mechanism`, `session_token_hygiene`, `expiry_rotation` |
| `authz` | Authorization | 16 | `per_request`, `object_level`, `policy_model` |
| `injection` | Injection & XSS | 14 | `query_safety`, `command_safety`, `output_encoding` |
| `input_validation` | Input validation | 12 | `boundary_validation`, `allowlists`, `upload_safety` |
| `secrets` | Secrets & config | 14 | `no_hardcode`, `injection_path`, `scanning` |
| `sensitive_data` | Sensitive data | 12 | `storage`, `log_redaction`, `transport_assumptions` |
| `deps_supply` | Dependencies | 8 | `lockfile`, `known_vuln_signal`, `update_practice` |
| `security_headers` | Transport & headers | 10 | `cors`, `csrf`, `headers_tls` |

Weights sum to 100.

## Evidence checklist

Auth middleware, object-level checks, SQL/HTML sinks, validators, `.env` samples, hashing, lockfiles, CORS/CSRF.

## Sub-criteria

| Dimension | Subs |
|-----------|------|
| `authn` | Sound mechanism; cookie/JWT hygiene; expiry/refresh/rotation |
| `authz` | Enforced every request; IDOR resistance; RBAC/ABAC clarity |
| `injection` | Parameterized queries; no unsafe shells; contextual output encoding |
| `input_validation` | Server-side validation; allowlists; upload limits/type checks |
| `secrets` | No live secrets in repo; env/manager injection; CI scanning |
| `sensitive_data` | Password/PII handling; log redaction; TLS assumptions noted |
| `deps_supply` | Lockfiles; obvious critical CVE age; update automation |
| `security_headers` | CORS least privilege; CSRF for cookie sessions; security headers / TLS N/A if unverifiable |

**Rule:** concrete authz hole or live secret → affected subs ≤3 + top summary.
