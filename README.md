# Globalization Skill

A reusable globalization skill for Codex and Claude Code, providing a 12-layer framework for i18n, locale, timezone, tenancy, compliance, billing, and region-aware architecture.

## Overview

This repository defines globalization as an engineering governance problem, not only a translation problem. The skill is designed for B2B2C and multi-tenant products that need to launch across languages, markets, jurisdictions, payment methods, and regions without rebuilding the architecture later.

The package is structured like a small library:

- `SKILL.md` contains activation rules, scope boundaries, and the load order.
- `references/getting-started.md` gives the shortest path for first-time use.
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

## What This Skill Is Not

- It is not only a translation or string-management skill.
- It is not a substitute for legal advice.
- It is not a country-by-country law database.
- It is not a promise that every stack, market, or provider combination is supported.

It is a governance and implementation framework that helps teams design global-ready systems and make capability gaps explicit.

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

## Quick Start

### Codex

```bash
git clone https://github.com/kcbehindbrand/globalization-skill.git ~/.agents/skills/globalization
```

### Claude Code

```bash
git clone https://github.com/kcbehindbrand/globalization-skill.git ~/.claude/skills/globalization
```

If the target folder already exists, update it with:

```bash
cd ~/.agents/skills/globalization && git pull
```

or:

```bash
cd ~/.claude/skills/globalization && git pull
```

## How To Use

Ask the assistant to apply the skill when a task touches:

- multilingual UI or localization architecture
- locale and time-zone resolution
- market or jurisdiction-aware product flows
- multi-tenant isolation and governance
- billing, invoicing, payment capability, or seller-role logic
- privacy, consent, residency, or rights workflows
- region-aware AI integration or provider capability decisions
- globalization launch review and observability

Typical prompts:

```text
Use the globalization skill to review this billing flow for market expansion.
```

```text
Apply the globalization framework before implementing this multilingual dashboard.
```

```text
Use the globalization skill to audit this Supabase schema for tenant isolation, locale fields, and privacy risks.
```

## Repository Structure

```text
SKILL.md
agents/
references/
  getting-started.md
  core/
  layers/
  adapters/
  checklists/
templates/
overlays/
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

Practical completion estimate:

- `80%` complete as a reusable globalization framework
- `50%` to `60%` complete as a business-ready operating standard until product-specific overlays are added

The highest-value next step is not more generic expansion. It is adding business-model overlays that bind the framework to a real product, tenant model, data flow, market scope, and billing mode.

## Notes

- GitHub Topics are repository settings and are not stored in this repository.
- Team-specific rules should go into `overlays/` rather than the core framework.
- Stack-specific implementation details should go into `references/adapters/`.
