# User Layer

## Scope

The user layer governs how people first encounter the product and how their locale, market, role, and identity context enter the system.

## Core Rules

- Treat entry point as part of globalization: landing pages, app stores, referrals, invitations, QR codes, and support links may all require locale continuity.
- Explicit user choices outrank inferred hints.
- Preserve the resolved locale and market context across sign-up, verification, onboarding, and the first authenticated surface.
- Roles such as `admin`, `member`, `viewer`, and `guest` affect journeys but must not implicitly rewrite locale or market intent.
- Different audience types should be modeled separately when relevant:
  - tenant operator
  - end consumer
  - internal staff
  - support or auditor

## Required Artifacts

- entry-point matrix by locale and market
- locale source precedence for anonymous and authenticated users
- role-to-journey map
- onboarding handoff rules

## Review Questions

- Can a user switch locale before authentication?
- Does locale continuity survive email verification and redirects?
- Are market-specific restrictions visible before a user enters a broken flow?
