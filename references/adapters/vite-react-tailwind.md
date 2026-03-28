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

## Recommended Library Shape

Examples in this adapter use `react-intl` because it aligns well with stable message keys, ICU interpolation, and extraction workflows. The framework still works with other libraries if they preserve the same invariants.

## Locale Bundle Example

```ts
const messageLoaders = import.meta.glob('../locales/*.json')

export async function loadMessages(locale: string) {
  const loader = messageLoaders[`../locales/${locale}.json`]
  if (!loader) throw new Error(`Unsupported locale: ${locale}`)
  const mod = await loader()
  return 'default' in mod ? mod.default : mod
}
```

## React-Specific Rules

- Use real Error Boundaries for localized failure surfaces.
- Recreate locale-bound formatter and i18n instances when locale changes.
- Avoid hydration mismatches caused by client-only locale detection.

## React Intl Example

```tsx
import { IntlProvider } from 'react-intl'

export function AppI18n({
  locale,
  dir,
  messages,
  children,
}: {
  locale: string
  dir: 'ltr' | 'rtl'
  messages: Record<string, string>
  children: React.ReactNode
}) {
  document.documentElement.lang = locale
  document.documentElement.dir = dir

  return (
    <IntlProvider locale={locale} messages={messages}>
      {children}
    </IntlProvider>
  )
}
```

## Tailwind-Specific Rules

- Prefer logical spacing and alignment abstractions where available.
- Audit utility usage for physical left/right assumptions.
- Test long strings, pseudolocale, and RTL screenshots.

## Direction-Safe Styling Example

```tsx
<div className="border-s ps-4 pe-3 text-start">
  <h2 className="truncate">{title}</h2>
</div>
```

Prefer logical utilities such as `ps-*`, `pe-*`, `ms-*`, `me-*`, `text-start`, and `border-s` over hardcoded left/right utilities when your Tailwind setup supports them.

## Review Checklist

- Can SSR and hydration agree on locale and direction?
- Are error states, loading states, and form validation localized?
- Can text expansion break component width or spacing?
