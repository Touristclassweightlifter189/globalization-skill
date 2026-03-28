# Globalization Skill

A reusable globalization skill for Codex and Claude Code, providing a 12-layer framework for i18n, locale, timezone, tenancy, compliance, billing, and region-aware architecture.

## Overview

This repository defines globalization as an engineering governance problem, not only a translation problem. The skill is designed for B2B2C and multi-tenant products that need to launch across languages, markets, jurisdictions, payment methods, and regions without rebuilding the architecture later.

The package is structured like a small library:

- `SKILL.md` contains activation rules, scope boundaries, and the load order.
- `references/core/` contains stable cross-stack rules.
- `references/layers/` contains the 12-layer framework.
- `references/adapters/` maps the core rules into named stacks.
- `references/checklists/` contains review gates.
- `templates/` contains reusable policy and schema skeletons.
- `overlays/` contains example team-policy extensions.

## 12-Layer Framework

1. User
2. Frontend / UI
3. Application Logic
4. API / Integration
5. Data
6. Auth & Security
7. Tenancy & Isolation
8. Compliance & Privacy
9. Billing & Subscription
10. Notification & Communication
11. Observability & Analytics
12. Infrastructure

## Policy Taxonomy

The skill separates four classes of rules:

- `standard`: formal standards such as BCP 47, IANA time zones, ISO 8601, and ISO 4217
- `official-guidance`: primary-source platform or vendor guidance
- `engineering-inference`: defensible engineering rules inferred from standards and official guidance
- `team-policy`: local operating policy for a product or organization

This separation prevents stack-specific habits or local policy choices from being presented as universal globalization doctrine.

## Installation

### Codex

Install into:

```bash
~/.agents/skills/globalization
```

### Claude Code

Install into:

```bash
~/.claude/skills/globalization
```

## Intended Use

Use this skill when planning, reviewing, or implementing:

- multilingual and multi-market products
- locale-aware frontend flows
- canonical API and data contracts
- multi-tenant SaaS platforms
- privacy and consent workflows
- international billing and invoicing
- region-aware AI integrations
- global-ready observability and infrastructure

## Status

This repository now contains a full first version of the framework, adapters, checklists, and templates. It is intended to be extended through adapters and overlays rather than by turning the core into a monolith.
