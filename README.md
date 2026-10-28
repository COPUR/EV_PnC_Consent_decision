# EV_PnC_Consent_decision

Roaming decision point (PDP): allow/deny for (driver, hub, purpose) at p95 ≤ 50 ms, fail closed.

Part of the **EV Owners Roaming Consent** project: a central, neutral consent registry and decision point for EV owners' roaming data (which hub may receive which data, for which purpose, under which KVKK safeguard). Repo family plan: `repo-plan/consent/README.md` in the project files.

## Scope

- Read model built from grant and safeguard events (CQRS)
- Local in-memory cache + Redis, invalidated by revocation events
- Every decision written asynchronously to the audit trail
- Load test at 2× target (1,000 → 2,000 decisions/s)

## Requirements

RC-GATE-002, RC-GATE-003, RC-NFR-001 (see `EV_PnC_Consent_docs`, specs from `roaming-consent/spec.md`)

## Tech stack

Java, Spring Boot 4, Redis

## Infrastructure (BOM)

Redis (cache), K8s HPA

## Scaling

Separate repo and deployable: hot read path with a different load profile and SLO than the registry; scales horizontally with no write dependency

## Ownership

Backend team B · Visibility: public · Wave 1: now (Phase 0–1, Nov 2026 – Feb 2027)

## Status

Scaffold only. Not production ready.

## License

Apache-2.0 (proposed)
