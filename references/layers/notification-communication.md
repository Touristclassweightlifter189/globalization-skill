# Notification & Communication Layer

## Scope

This layer covers in-app notifications, email, SMS, push, and other external communications.

## Core Rules

- Separate transactional, operational, and marketing purposes.
- Model preferences per purpose and per channel when required.
- Localize templates through stable keys and interpolation, not message concatenation.
- Respect quiet hours and time-zone-aware delivery windows when the channel or market requires it.
- Queue or event-drive notifications rather than blocking the main request path.
- Keep regulated notices distinct from promotional communication.
- Log delivery intent and outcome without leaking unnecessary personal content.

## Required Artifacts

- notification purpose model
- channel preference matrix
- template governance rules
- delivery and retry policy

## Review Questions

- Which events trigger messages, and which should not?
- Are quiet hours resolved from the right time zone?
- Could a failed notification block the primary user flow?
