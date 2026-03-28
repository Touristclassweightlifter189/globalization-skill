# Metadata Event Schema Template

## Purpose

Use this template for event or insert metadata that needs globalization context.

## Required Fields

```json
{
  "tenant_id": "",
  "channel": "",
  "language_tag": "",
  "locale": "",
  "dir": "",
  "time_zone": "",
  "market_country": "",
  "jurisdiction": "",
  "serving_region": "",
  "residency_region": "",
  "locale_source": ""
}
```

## Optional Fields

```json
{
  "role": "",
  "currency_code": "",
  "legal_basis": "",
  "consent_state": "",
  "device_class": "",
  "browser_language": ""
}
```

## Notes

- Governance-critical fields should also exist as typed columns when they are used in policy or query logic.
- Avoid storing raw user-agent strings unless there is a justified and governed need.
