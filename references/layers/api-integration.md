# API / Integration Layer

## Scope

This layer governs how systems exchange data, negotiate locale context, and integrate with internal or external services.

## Core Rules

- APIs should exchange canonical machine values first.
- Localized display fields may be returned, but they must not replace canonical fields.
- Locale negotiation should be explicit when responses depend on it.
- Webhooks and event consumers should be treated as at-least-once and potentially out-of-order.
- Verify webhook authenticity and deduplicate idempotently.
- Maintain capability matrices for provider support by market, region, feature, and currency when relevant.
- Use stable error codes and predictable envelopes where the product standard requires it.
- Distinguish:
  - access support
  - feature support
  - regional processing behavior

## Required Artifacts

- canonical request and response contract
- locale negotiation policy
- webhook retry and dedupe strategy
- provider capability matrix

## Review Questions

- Could a downstream consumer reconstruct canonical meaning without localized strings?
- Is region support being assumed or documented?
- Are integration timeouts and fallback behaviors explicit?
