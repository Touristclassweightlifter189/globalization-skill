# Data Layer

## Scope

The data layer defines how canonical values, localized variants, and metadata are modeled and retained.

## Core Rules

- Use canonical identifiers or standard codes as the source of truth.
- Do not use localized UI labels as primary keys or durable business values.
- Model localizable content separately from canonical entities.
- Use UTC timestamps for machine exchange and audit.
- Store the relevant IANA time zone separately when civil-time interpretation matters.
- Use typed columns for governance-critical dimensions such as locale, market, tenant, legal basis, and seller role.
- Use extensible metadata fields only for non-authoritative or additive detail.
- Normalize Unicode and choose collation consciously for search and equality behavior.
- Define retention and deletion policy per data class.

## Required Artifacts

- canonical schema model
- localization storage model
- time and timezone model
- retention and anonymization model

## Review Questions

- Can the same entity be represented in multiple languages without duplicating the business identity?
- Are governance dimensions queryable without parsing opaque JSON?
- Is time stored in a way that supports both audit and user display?
