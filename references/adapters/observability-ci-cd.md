# Observability CI/CD Adapter

## Purpose

Maps the framework into structured telemetry, CI validation, and release gating.

## Mapping Rules

- Use structured JSON logs or equivalent structured telemetry.
- Propagate W3C trace context end to end where possible.
- Capture canonical globalization attributes such as resolved locale, locale source, market, region, direction, and fallback depth.
- Segment SLOs by user-relevant region or market when behavior differs materially.
- Treat globalization-affecting changes as release-gated changes.

## CI/CD Rules

- Run locale extraction or consistency checks when the stack supports them.
- Verify missing keys, broken ICU syntax, and structural mismatch across locale files.
- Include pseudolocale, RTL, and time-zone or market-specific test coverage.
- Prefer canary rollouts for changes that affect routing, formatting, billing logic, or provider regioning.
- Keep schema changes as reviewed migration files, not UI-only drift.

## Review Checklist

- Could CI detect missing locale keys or hydration drift?
- Could operations isolate a market-specific failure quickly?
- Is there evidence attached to the release decision?
