# Observability & Analytics Layer

## Scope

This layer measures globalization-critical behavior and release safety across markets, regions, and locales.

## Core Rules

- Emit structured logs for globalization-critical paths.
- Propagate trace context across services and async work where possible.
- Segment dashboards and SLOs by region, market, locale, and channel where those dimensions affect user experience.
- Measure fallback depth, locale resolution source, and translation or formatting failures.
- Use pseudolocale, RTL, and time-zone test coverage in release verification.
- Redact secrets, tokens, and unnecessary personal data from telemetry.
- Separate product analytics from compliance-sensitive processing when necessary.

## Required Artifacts

- telemetry attribute schema
- segmented SLO definition
- globalization test coverage map
- redaction and retention policy

## Review Questions

- Could you detect a localization failure in one market without waiting for support tickets?
- Are traces and logs sufficient to debug locale resolution and fallback behavior?
- Is telemetry residency aligned with product promises?
