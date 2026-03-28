# Supabase Postgres RLS Adapter

## Purpose

Maps the core globalization model into Supabase, PostgreSQL, RLS, and Edge Functions.

## Mapping Rules

- Store governance-critical dimensions in typed columns, not only in `jsonb`.
- Use `TIMESTAMPTZ` for audit and exchange timestamps.
- If business logic depends on civil time, store the relevant IANA time zone separately.
- Prefer explicit locale columns and avoid truncating locale identifiers.
- Use conscious collation strategy for locale-sensitive search and comparison.

## Concrete Schema Example

```sql
create table public.reviews (
  id bigint generated always as identity primary key,
  tenant_id uuid not null,
  author_user_id uuid not null,
  language_tag text not null,
  locale text not null,
  time_zone text,
  market_country text not null,
  rating integer not null check (rating between 1 and 5),
  body text,
  metadata jsonb not null default '{}'::jsonb,
  created_at timestamptz not null default now()
);

create index reviews_tenant_id_idx on public.reviews (tenant_id);
create index reviews_language_tag_idx on public.reviews (language_tag);
```

## RLS Rules

- Tenant isolation predicates belong in both `USING` and `WITH CHECK` policies.
- Guard against `auth.uid()` being null.
- Test RLS as a real user, not only as table owner or privileged role.
- Be careful with views. Default view behavior can bypass expectations unless `security_invoker` or equivalent behavior is set deliberately.
- Authorization decisions should use immutable claims, not mutable profile metadata.

## Concrete RLS Example

```sql
alter table public.reviews enable row level security;

create policy "tenant members can read reviews"
on public.reviews
for select
using (
  auth.uid() is not null
  and tenant_id = ((auth.jwt() -> 'app_metadata' ->> 'tenant_id')::uuid)
);

create policy "tenant members can insert reviews"
on public.reviews
for insert
with check (
  auth.uid() is not null
  and tenant_id = ((auth.jwt() -> 'app_metadata' ->> 'tenant_id')::uuid)
  and author_user_id = auth.uid()
);
```

## Edge Function Rules

- Separate user-scoped clients from service-role clients.
- Treat Edge Functions as region-sensitive execution points. Do not assume the nearest region is always the compliant one for regulated processing.
- Verify webhook signatures explicitly.
- Do not rely on database webhooks as your main governance enforcement layer.

## Edge Function Example

```ts
import { createClient } from '@supabase/supabase-js'

const authHeader = req.headers.get('Authorization') ?? ''

const userClient = createClient(
  Deno.env.get('SUPABASE_URL')!,
  Deno.env.get('SUPABASE_ANON_KEY')!,
  { global: { headers: { Authorization: authHeader } } }
)

const serviceClient = createClient(
  Deno.env.get('SUPABASE_URL')!,
  Deno.env.get('SUPABASE_SERVICE_ROLE_KEY')!
)
```

Use `userClient` for tenant-scoped reads and writes that must respect RLS. Use `serviceClient` only for explicitly privileged flows with their own authorization checks.

## Review Checklist

- Is tenant scope enforced in table policies and write paths?
- Are locale, market, and seller-role fields queryable without parsing metadata?
- Are logs and webhook traces redacted?
