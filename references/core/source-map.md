# Source Map

## Purpose

This file lists the main source families behind the framework. It is a navigation aid, not a legal opinion.

## Standards

- BCP 47 for language tags
- IANA Time Zone Database for time-zone identifiers
- ISO 8601 for machine-readable date and time exchange
- ISO 4217 for currency codes
- W3C Trace Context for trace propagation
- ICU MessageFormat and CLDR-related conventions for localization practice

## Official Guidance Families

- browser and frontend platform guidance for `lang`, `dir`, and international formatting
- OAuth 2.0, OIDC, and PKCE guidance for modern auth flows
- PostgreSQL and Supabase guidance for typed schema, RLS, and security behavior
- provider guidance for webhooks, retries, and capability limits
- OpenTelemetry guidance for structured telemetry

## Engineering Inference Families

- capability matrices for providers, markets, and regions
- explicit user choice over environment hints
- canonical machine data separated from localized presentation
- region-aware rollouts and segmented SLOs

## Team-Policy Inputs

- supported markets
- supported languages
- supported payment methods
- fallback strategy
- risk tolerance and launch-gate criteria
