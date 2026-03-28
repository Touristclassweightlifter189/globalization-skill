# Dimension Catalog

## Purpose

These dimensions appear across layers. They should be named consistently and stored in typed fields when they are governance-critical.

## Dimensions

### Identity and audience

- `tenant_id`: primary tenant, organization, store, or workspace identifier
- `workspace_id`: secondary scope when a tenant contains multiple workspaces
- `role`: authorization or audience role
- `channel`: web, mobile, email, SMS, API, webhook, internal tool, or other delivery path

### Language and presentation

- `language_tag`: BCP 47 language identifier used for content selection
- `locale`: resolved application locale used by rendering and formatting
- `dir`: document direction, typically `ltr` or `rtl`
- `locale_source`: which precedence source resolved the locale

### Geography and serving model

- `market_country`: market of sale or supported commercial surface
- `jurisdiction`: legal or tax jurisdiction relevant to the operation
- `serving_region`: where the service is delivered from
- `residency_region`: where regulated data must reside

### Time and money

- `time_zone`: IANA time zone associated with the user, tenant, or business rule
- `currency_code`: ISO 4217 presentment or settlement currency

### Privacy and processing

- `legal_basis`: lawful basis for the relevant processing activity
- `consent_state`: consent or preference state for the specific purpose

## Modeling Rules

- Use typed columns for governance-critical dimensions.
- Use metadata objects only for extensible or non-authoritative details.
- Keep canonical identifiers stable even if localized labels change.
- Preserve the distinction between market, jurisdiction, and region. They are not interchangeable.
