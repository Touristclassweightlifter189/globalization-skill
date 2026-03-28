# Vite React Tailwind Adapter

## Purpose

Maps the framework into a Vite plus React plus Tailwind frontend.

## Mapping Rules

- Resolve locale before or during first render in a deterministic way.
- Use one locale contract for route state, i18n provider, document metadata, and formatters.
- Keep translation keys statically extractable.
- Use logical CSS properties and direction-safe utility patterns as the default.
- Treat `rtl:` and `ltr:` variants as escape hatches, not the baseline architecture.
- Use `import.meta.glob` or an equivalent loader for locale bundles.

## React-Specific Rules

- Use real Error Boundaries for localized failure surfaces.
- Recreate locale-bound formatter and i18n instances when locale changes.
- Avoid hydration mismatches caused by client-only locale detection.

## Tailwind-Specific Rules

- Prefer logical spacing and alignment abstractions where available.
- Audit utility usage for physical left/right assumptions.
- Test long strings, pseudolocale, and RTL screenshots.

## Review Checklist

- Can SSR and hydration agree on locale and direction?
- Are error states, loading states, and form validation localized?
- Can text expansion break component width or spacing?
