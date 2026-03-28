# Capacitor Mobile Adapter

## Purpose

Maps the framework into a Capacitor-based mobile or hybrid application.

## Core Rules

- Keep locale, direction, and formatting under the same canonical contract used by the web app.
- Distinguish app locale, device locale, store metadata locale, and notification locale.
- Do not assume device locale should override an explicit in-app user choice.
- Treat push notification language and quiet-hour behavior as part of the notification layer, not only platform setup.

## Locale Detection Example

```ts
import { Device } from '@capacitor/device'

export async function getDeviceLocale() {
  const info = await Device.getLanguageCode()
  return info.value
}
```

Use the device language only as an input into the precedence model. Persist explicit user choice separately.

## App Shell Example

```ts
document.documentElement.lang = resolvedLocale
document.documentElement.dir = resolvedDir
```

Apply this as early as possible during app bootstrap to avoid mixed-direction flashes or incorrect formatter defaults.

## Mobile-Specific Concerns

- verify App Store and Play Store metadata by market and locale
- localize permission rationale and OS-facing strings
- confirm push templates by locale and platform
- test offline or delayed-sync flows with canonical timestamps
- define what happens when device locale changes after login

## Review Checklist

- Does the app preserve explicit locale choice across reinstalls or device changes when expected?
- Are push notifications localized by the right source of truth?
- Are store metadata, screenshots, and app descriptions aligned with supported locales?
