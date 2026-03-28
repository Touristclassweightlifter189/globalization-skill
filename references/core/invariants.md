# Invariants

## Invariants

The following rules are expected unless a stricter standard or law applies.

### Language and UI

- All user-facing product copy should come from stable translation keys.
- Dynamic values should be inserted through interpolation, not string concatenation.
- The root document should reflect the resolved locale and direction.
- Direction-safe layout primitives and logical CSS properties are the default.

### Data and time

- Canonical data should be locale-neutral where possible.
- Timestamps should be stored in UTC for exchange and audit.
- If civil-time meaning matters, store the relevant IANA time zone separately.
- Localized display strings should not be the only representation of important values.

### Identity and isolation

- Every tenant-scoped read or write should carry tenant scope explicitly.
- Authorization decisions should be based on immutable claims or trusted server-side state.
- JWTs should not contain unnecessary PII.

### Privacy and compliance

- Data collection should be tied to an explicit purpose.
- Lawful basis and consent should be modeled explicitly where required.
- Anonymization or pseudonymization should be deliberate and auditable.

### Billing

- Seller role should be explicit.
- Payment method support should be capability-driven, not assumed.
- Issued invoices and adjustments should preserve immutable lineage.

### Observability

- Globalization-critical paths should emit structured telemetry.
- Logs must avoid leaking secrets or unnecessary personal data.
