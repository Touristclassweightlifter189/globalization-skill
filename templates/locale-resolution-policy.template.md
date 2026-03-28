# Locale Resolution Policy Template

## Purpose

Define how the product resolves locale and direction for a given surface.

## Policy

- Surface:
- Audience:
- Supported locales:
- Default locale:
- Direction policy:

## Resolution Order

1. Explicit user choice:
2. Persisted preference:
3. Route or domain:
4. Tenant or workspace policy:
5. Market default:
6. `Accept-Language`:
7. Final fallback:

## Notes

- Locale source field:
- Fallback behavior:
- Unsupported locale behavior:

## Example

- Surface: dashboard web app
- Audience: authenticated store staff
- Supported locales: `en`, `zh-Hant`
- Default locale: `en`
- Direction policy: derive from resolved locale

Resolution order:

1. explicit in-app user selection
2. persisted profile preference
3. tenant default
4. `Accept-Language`
5. product default `en`

Notes:

- Locale source field: `locale_source`
- Fallback behavior: soft fallback to `en` for unsupported locales
- Unsupported locale behavior: preserve canonical data and log unsupported requests
