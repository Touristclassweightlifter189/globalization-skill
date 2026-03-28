# Frontend / UI Layer

## Scope

The frontend layer is responsible for presenting the resolved globalization contract consistently and safely.

## Core Rules

- Use one canonical locale contract to drive route locale, i18n provider, `<html lang>`, `<html dir>`, and formatters.
- Do not hardcode display strings in components.
- Do not use computed translation keys or sentence assembly in render code.
- Use interpolation for dynamic values.
- Prefer logical CSS properties and direction-safe primitives.
- Use bidi isolation where user-generated or mixed-direction text can appear inside surrounding text.
- Test text expansion and truncation. Truncation is allowed only for preview surfaces with an accessible reveal path.
- Localize loading, empty, validation, and error states.
- Build forms that support global names, addresses, phone numbers, and postal codes without Western-only assumptions.
- Frontend rendering should format dates, numbers, and currency for the user-facing surface using the resolved locale and time zone.
- Backend formatting is allowed only for fixed artifacts such as invoices, PDFs, or finalized emails when locale and time zone are explicit inputs.

## Required Artifacts

- locale-to-document contract
- direction-safe layout policy
- pseudolocale and RTL test coverage
- hydration-safe locale initialization flow

## Review Questions

- Can first render be reproduced deterministically in SSR and hydration?
- Does changing locale recreate formatters and document metadata?
- Can long translated labels or mixed-direction content break layout?
