# Supabase Postgres RLS Adapter

## Purpose

Maps the core globalization model into Supabase, PostgreSQL, RLS, and Edge Functions.

## Mapping Rules

- Store governance-critical dimensions in typed columns, not only in `jsonb`.
- Use `TIMESTAMPTZ` for audit and exchange timestamps.
- If business logic depends on civil time, store the relevant IANA time zone separately.
- Prefer explicit locale columns and avoid truncating locale identifiers.
- Use conscious collation strategy for locale-sensitive search and comparison.

## RLS Rules

- Tenant isolation predicates belong in both `USING` and `WITH CHECK` policies.
- Guard against `auth.uid()` being null.
- Test RLS as a real user, not only as table owner or privileged role.
- Be careful with views. Default view behavior can bypass expectations unless `security_invoker` or equivalent behavior is set deliberately.
- Authorization decisions should use immutable claims, not mutable profile metadata.

## Edge Function Rules

- Separate user-scoped clients from service-role clients.
- Treat Edge Functions as region-sensitive execution points. Do not assume the nearest region is always the compliant one for regulated processing.
- Verify webhook signatures explicitly.
- Do not rely on database webhooks as your main governance enforcement layer.

## Review Checklist

- Is tenant scope enforced in table policies and write paths?
- Are locale, market, and seller-role fields queryable without parsing metadata?
- Are logs and webhook traces redacted?
