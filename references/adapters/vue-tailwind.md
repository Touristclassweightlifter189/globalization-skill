# Vue Tailwind Adapter

## Purpose

Maps the framework into a Vue plus Tailwind frontend.

## Mapping Rules

- Use a single resolved locale contract to drive router state, Vue I18n state, root document metadata, and formatters.
- Keep translation keys static and extractable.
- Prefer logical and direction-safe styling choices in Tailwind.
- Handle locale change as a first-class state transition, not a cosmetic toggle.

## Vue-Specific Rules

- Use `errorCaptured` and `app.config.errorHandler` to localize and report failures.
- Watch route or app state for locale changes and recreate locale-bound formatters when needed.
- Be explicit about local versus global i18n scope.
- In SSR, guard against Suspense or async locale loading paths that can cause hydration mismatch.

## Review Checklist

- Does changing locale update `lang`, `dir`, and formatting together?
- Can nested component scopes drift from the global locale contract?
- Are fallback chains explicit and testable?
