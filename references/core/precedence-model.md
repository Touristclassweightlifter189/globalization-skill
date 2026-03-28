# Precedence Model

## Purpose

Globalization decisions often conflict. This file defines which source wins when multiple inputs disagree.

## Rule Precedence

From highest to lowest:

1. legal or regulatory obligations for the applicable jurisdiction
2. security, privacy, and tenant-isolation invariants
3. contractual product commitments and supported capability matrices
4. explicit user choices
5. organization or workspace settings
6. market defaults
7. platform hints such as browser language, OS locale, or IP-derived geography
8. presentation preferences and cosmetic fallbacks

## Locale Resolution Precedence

For request-time locale resolution, use this order unless a product overlay says otherwise:

1. explicit in-session user selection
2. persisted user preference
3. route, subpath, or domain locale
4. workspace or tenant policy if the product is tenant-configured
5. accepted market default for the serving surface
6. `Accept-Language`
7. final product default

## Time-Zone Resolution Precedence

1. explicit user profile time zone
2. workspace or tenant time zone where the experience is tenant-scoped
3. market or service time zone for business rules that depend on civil time
4. device hint for display only
5. fallback product default

Never use a display time zone as the only stored record when civil time has business meaning. Store UTC plus the relevant IANA time zone.

## Currency Resolution Precedence

1. contractual or regulated billing currency
2. seller or merchant capability matrix
3. market presentment default
4. display-only preference

## Conflict Resolution Guidance

- If a higher-precedence source is absent, fall through explicitly.
- Log the final resolved source in `locale_source` or the equivalent field.
- Never silently replace an explicit user choice with a hint-based fallback.
- If a requested combination is unsupported, fail with a clear explanation instead of pretending support.
