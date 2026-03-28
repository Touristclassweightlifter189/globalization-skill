---
name: globalization
description: Use when designing or implementing global-ready systems that require i18n, locale, timezone, compliance, tenancy, billing, or region-aware architecture.
---

# Globalization

Use this skill when a task touches any of the following:

- multilingual UI or content delivery
- locale or time-zone resolution
- global or region-aware APIs
- canonical data modeling for multi-market systems
- privacy, consent, or residency constraints
- billing, tax, invoicing, or seller-of-record logic
- tenant isolation across organizations, stores, or workspaces
- region-aware observability, rollout, or infrastructure

## Scope

This skill defines a 12-layer globalization framework for B2B2C and multi-tenant products. It is broader than i18n. It covers the user journey, UI, logic, APIs, data, security, privacy, billing, notifications, analytics, and infrastructure needed to ship global-ready software safely.

## Hard Boundaries

- Do not treat team policy as a formal standard.
- Do not give legal advice. State the engineering implication and flag where legal review is required.
- Do not infer law, tax, or compliance obligations from `Accept-Language` alone.
- Do not collapse country access, regional processing, and data residency into one vague "region" concept.
- Do not assume backend-only or frontend-only ownership of formatting, privacy, or billing concerns. Resolve responsibility explicitly.

## Load Order

Start with `SKILL.md` only, then load the minimum set of references needed.

Always load:

1. `references/core/framework-overview.md`
2. `references/core/policy-taxonomy.md`

Load next based on task shape:

- If the task is about conflict resolution, rule priority, or fallback order:
  - `references/core/precedence-model.md`
- If the task needs schema, event, or metadata design:
  - `references/core/dimension-catalog.md`
  - `references/core/invariants.md`
- If the task is an architecture or product review:
  - only the relevant files under `references/layers/`
- If the task names a stack or the stack is clearly implied:
  - only the relevant file under `references/adapters/`
- If the task is launch readiness or code review:
  - only the relevant file under `references/checklists/`
- If the task needs a reusable document or schema:
  - only the relevant file under `templates/`
- If the task is organization-specific:
  - only the relevant file under `overlays/`

## Core Non-Negotiables

- Use canonical locale identifiers and codes:
  - `language_tag` uses BCP 47
  - `time_zone` uses IANA names
  - timestamps use ISO 8601 and UTC for machine exchange
  - `currency_code` uses ISO 4217
- Resolve locale as a single application contract. The resolved locale must drive route locale, i18n provider, formatting, and root document metadata.
- Do not hardcode UI copy in product surfaces. Use stable translation keys and interpolation for dynamic values.
- Do not build LTR-only layouts. Prefer logical CSS properties and direction-safe primitives.
- Store canonical values in data and APIs. Localized display strings are derivatives, not the source of truth.
- Treat tenant isolation as a first-class concern across logic, data, and auth, not as a side effect.
- Treat privacy, consent, and lawful basis as explicit fields and workflows, not implied states.
- Treat billing as jurisdiction-aware state and document logic, not only as a payment gateway callback.
- Instrument globalization-critical paths with structured telemetry.

## Delivery Workflow

1. Classify the task:
   - `core governance`
   - `layer-specific design`
   - `stack implementation`
   - `team policy`
2. Load only the minimum references for that class.
3. Before producing code, state the relevant globalization constraints for the task.
4. Implement or review the change.
5. Verify against the relevant checklist before declaring completion.

## When To Escalate

Escalate for human review when:

- a requirement creates legal or regulatory ambiguity
- a residency claim cannot be grounded in a primary source
- a tax or invoice obligation changes by market or seller role
- the product needs a new market, language, or payment method without an existing capability matrix
- a proposed change weakens tenant isolation, privacy controls, or auditability
