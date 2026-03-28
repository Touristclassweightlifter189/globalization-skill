# Policy Taxonomy

## Purpose

Every rule in this skill should be understood as one of four classes. This keeps claims precise and prevents accidental overreach.

## Rule Classes

### `standard`

Formal standards or specifications with stable identifiers.

Examples:

- BCP 47 language tags
- IANA time-zone database
- ISO 8601 timestamps
- ISO 4217 currency codes
- W3C Trace Context

Use when:

- choosing field semantics
- validating canonical codes
- defining machine contracts

### `official-guidance`

Primary-source platform, framework, or vendor guidance.

Examples:

- framework guidance for locale rendering
- platform guidance for security and auth
- provider documentation for region availability or webhooks

Use when:

- implementing against a named platform
- making claims about vendor behavior

### `engineering-inference`

An engineering rule derived from standards, official guidance, and operational evidence.

Examples:

- "explicit user locale choice outranks browser hints"
- "localized display strings are not the source of truth"
- "provider availability should be maintained as a capability matrix"

Use when:

- the engineering rule is not itself a formal standard
- a policy needs to be generalized across stacks

### `team-policy`

A local decision made by a product, organization, or workspace.

Examples:

- supported languages and markets
- consent defaults
- allowed fallback behavior
- invoice numbering strategy inside legal boundaries

Use when:

- the product has chosen one path among several valid ones

## Writing Rules

When documenting or applying a rule:

- label the class when ambiguity matters
- do not present `team-policy` as universal guidance
- do not present `engineering-inference` as a law or formal standard
- prefer primary sources for `official-guidance`

## Conflict Handling

- `standard` and law-like obligations outrank all local preference
- `official-guidance` constrains stack-specific implementation
- `engineering-inference` fills the gaps between standards and implementation
- `team-policy` customizes within the permitted space
