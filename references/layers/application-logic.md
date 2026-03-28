# Application Logic Layer

## Scope

This layer handles state transitions, validation, entitlement checks, quotas, and business rules.

## Core Rules

- Separate locale-neutral invariants from jurisdiction-sensitive or market-sensitive policy.
- Do not derive legal or commercial policy from `Accept-Language`.
- Represent lifecycle changes as explicit state machines where regulated or audit-sensitive behavior exists.
- Make mutating operations idempotent.
- Validation should operate on canonical values before presentation formatting.
- Business logic should operate on typed identifiers and canonical status values, not localized labels.
- Fallback logic should be explicit and auditable.

## Required Artifacts

- business-rule catalog
- policy overlay points
- state machine definitions for regulated flows
- idempotency key policy

## Review Questions

- Which rules are global invariants and which are overlays?
- Can the same request be retried safely?
- Are unsupported markets or channels rejected explicitly instead of silently degraded?
