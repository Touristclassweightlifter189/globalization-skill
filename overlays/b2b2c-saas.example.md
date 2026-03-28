# B2B2C SaaS Example Overlay

## Product Model

- Product name: Example Reviews Platform
- Product type: B2B2C
- Primary customer: store owner
- Secondary end user: consumer leaving a review or receiving communication

## Tenant Model

- Primary tenant unit: `store_id`
- Secondary workspace unit: `workspace_id`
- End-user relationship to tenant: consumers belong to no tenant but interact with a tenant-owned surface
- Cross-tenant admin roles: internal support only, fully audited

## User Roles

- Anonymous: consumer before login
- Guest: invited collaborator before activation
- Member: store staff
- Admin: store owner or workspace admin
- Internal operator: support or compliance operator
- Support or auditor: read-restricted internal role

## Market Scope

- Initial markets: US, HK, SG
- Initial languages: en, zh-Hant
- Initial currencies: USD, HKD, SGD
- Initial serving regions: us, ap-southeast
- Residency constraints: no special residency promise in v1

## Revenue Model

- Seller role: direct merchant
- Billing model: subscription plus usage-based AI features
- Payment providers: Stripe for subscriptions, OpenAI for AI usage
- Invoice requirements: PDF invoice in supported markets, tax evidence retained per billing event

## Data Model

- Core entities: stores, workspaces, reviews, campaigns, invoices, notification events
- Localized entities: review templates, marketing copy, notification templates
- Sensitive data classes: account identity, billing contact, support logs
- Required metadata fields: tenant_id, locale, market_country, channel, time_zone

## Notification Model

- Transactional notifications: verification email, invoice email, payout alert
- Operational notifications: review digest, failed integration alert
- Marketing notifications: feature launch, upgrade prompts
- Restricted channels or markets: marketing requires explicit opt-in where policy says so

## AI Feature Model

- AI-powered features: review summarization, reply drafting, campaign copy generation
- Supported locales: en, zh-Hant in v1
- Provider and region constraints: fallback disabled when residency or unsupported-region constraints apply
- Human review triggers: regulated or public-facing generated copy for unsupported locales

## Operating Rules

- Unsupported market behavior: block checkout and show supported-market message
- Unsupported locale behavior: fall back to default locale but preserve canonical data
- Risk tolerance: fail closed on billing and compliance, fail soft on non-critical marketing content
- Launch gate owner: product plus engineering
