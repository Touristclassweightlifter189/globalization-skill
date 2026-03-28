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

## Capability Matrix Example

```json
{
  "country": "SG",
  "project_region": "us",
  "endpoint": "responses",
  "model": "gpt-4.1-mini",
  "feature": "reply_drafting",
  "supported": true,
  "residency_claim_allowed": false,
  "fallback_model": "gpt-4.1-mini",
  "fallback_mode": "same-region-or-fail"
}
```

## Reliability Rules

- Use bounded retries and timeouts.
- Acknowledge provider webhooks quickly and process asynchronously.
- Deduplicate webhook events using provider event identifiers.
- Design explicit fallback behavior for unsupported countries, models, regions, or safety states.
- Do not silently reroute a regulated workflow into an unsupported region.

## Fallback Example

```ts
type Capability = {
  supported: boolean
  fallbackModel?: string
  fallbackMode: 'same-region-or-fail' | 'template-only'
}

export async function generateReply({
  openai,
  capability,
  input,
}: {
  openai: any
  capability: Capability
  input: string
}) {
  if (!capability.supported) {
    if (capability.fallbackMode === 'template-only') {
      return { mode: 'template', output: 'Thanks for your feedback.' }
    }
    throw new Error('Unsupported market, region, or feature combination')
  }

  const controller = new AbortController()
  const timeout = setTimeout(() => controller.abort(), 8000)

  try {
    const response = await openai.responses.create(
      {
        model: capability.fallbackModel ?? 'gpt-4.1-mini',
        input,
      },
      { signal: controller.signal }
    )

    return { mode: 'model', output: response.output_text }
  } finally {
    clearTimeout(timeout)
  }
}
```

Use this pattern only when the fallback path is policy-approved. If compliance or residency rules disallow fallback, fail closed.

## Review Checklist

- What exact claim is being made about availability or residency?
- What is the fallback path if the preferred feature is unavailable?
- Has the localized quality and safety threshold been evaluated for the target locale?
