 # Globalization Skill

  A reusable globalization skill for Codex and Claude Code, providing a 12-layer framework for
  i18n, locale, timezone, tenancy, compliance, billing, and region-aware architecture.

  ## Overview

  This repository defines a globalization skill designed for AI coding assistants. It is not
  limited to translation or i18n. It provides a broader governance framework for building global-
  ready products across product flows, frontend, backend, data, privacy, billing, observability,
  and infrastructure.

  The goal is to make globalization a first-class engineering standard from the beginning, so
  future features, languages, markets, and regions can be added without reworking the foundation.

  ## What This Skill Covers

  The skill is organized around a 12-layer globalization framework:

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

  It also defines cross-cutting standards for:

  - language tags
  - locale handling
  - text direction
  - time zones
  - currency
  - market and jurisdiction
  - tenant isolation
  - consent and legal basis
  - metadata and event design
  - region-aware delivery and operations

  ## Philosophy

  This skill treats globalization as an architecture and governance problem, not just a
  translation problem.

  It separates:

  - formal standards
  - official platform guidance
  - engineering inferences
  - team policy

  That separation helps prevent local implementation choices from being mistaken for universal
  rules.

  ## Repository Structure

  ```text
  SKILL.md
  agents/
  references/
  templates/
  overlays/

  ## Installation

  ### Codex

  Install into:

  ~/.agents/skills/globalization

  Example:

  git clone https://github.com/<your-account>/globalization-skill.git ~/.agents/skills/globalizat
  ion

  ### Claude Code

  Install into:

  ~/.claude/skills/globalization

  Example:

  git clone https://github.com/<your-account>/globalization-skill.git ~/.claude/skills/globalizat
  ion

  ## Intended Use

  Use this skill when designing or implementing:

  - multilingual products
  - locale-aware UI and formatting
  - global data models
  - multi-tenant SaaS platforms
  - privacy and compliance workflows
  - international billing and invoicing
  - region-aware AI or API integrations
  - global-ready analytics and infrastructure

  ## Status

  This repository is being structured as a reusable library-style skill. The framework is designed
  to be expanded with stack adapters, templates, and policy overlays while keeping the core rules
  stable.

  ## License

  MIT
