# OpenAI Adapter

## Purpose

Maps the framework into OpenAI-backed features without flattening provider capability and compliance concerns.

## Mapping Rules

- Distinguish country access, regional feature availability, project region, and data-processing claims.
- Do not claim in-region residency or processing unless the exact feature and deployment path support that claim.
- Model provider capability as a matrix:
  - country
  - project region
  - endpoint
  - model or model snapshot
  - feature
- Treat locale safety as a per-locale evaluation problem, not a single global safety threshold.
- Validate prompt and output quality with native-language evaluation where the feature depends on localized quality.

## Reliability Rules

- Use bounded retries and timeouts.
- Acknowledge provider webhooks quickly and process asynchronously.
- Deduplicate webhook events using provider event identifiers.
- Design explicit fallback behavior for unsupported countries, models, regions, or safety states.
- Do not silently reroute a regulated workflow into an unsupported region.

## Review Checklist

- What exact claim is being made about availability or residency?
- What is the fallback path if the preferred feature is unavailable?
- Has the localized quality and safety threshold been evaluated for the target locale?
