# Anti-Patterns

## Anti-Patterns

- Hardcoding UI copy in components or templates.
- Building sentences by concatenating translated fragments and dynamic values.
- Using `margin-left`, `padding-right`, or other physical CSS properties as the default layout approach.
- Treating `Accept-Language` as legal jurisdiction.
- Treating IP-derived geography as a trustworthy substitute for explicit user or billing data.
- Returning only formatted display strings from APIs when downstream systems need canonical values.
- Using localized text as the database source of truth for tags, personas, categories, or states.
- Storing only a browser or device local time without UTC.
- Hiding tenant, locale, market, or consent governance fields only inside opaque JSON.
- Assuming a payment processor or AI provider supports every market, currency, or region uniformly.
- Treating invoices as mutable UI artifacts instead of regulated records.
- Sending notifications synchronously on the request path when they should be queued or event-driven.
- Logging tokens, raw webhook bodies, or user-identifying payloads without minimization.
