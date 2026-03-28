# Getting Started

Use this file when opening the skill for the first time and you need the shortest path to action.

## Read Order

1. `SKILL.md`
2. `references/getting-started.md`
3. `references/core/framework-overview.md`
4. `references/core/policy-taxonomy.md`

After that, choose only one branch:

- Architecture or product review:
  - read the relevant file under `references/layers/`
- Stack implementation:
  - read the relevant file under `references/adapters/`
- Launch or code review:
  - read the relevant file under `references/checklists/`
- Product-specific configuration:
  - read the relevant file under `overlays/`

## Recommended First Pass For New Projects

1. Define supported markets, languages, currencies, and regions.
2. Define tenant model and user roles.
3. Decide locale, time-zone, and currency precedence.
4. Define canonical entities and localized entities.
5. Confirm seller role and billing model.
6. Add a business overlay before coding large features.

## Minimum Files To Touch

For a new project, start by filling or reviewing:

- `templates/locale-resolution-policy.template.md`
- `templates/capability-matrix.template.md`
- `overlays/business-model-overlay.template.md`
- the one adapter file that matches your stack

## Shortcut By Task Type

### Multilingual UI

- `references/layers/frontend-ui.md`
- `references/adapters/vite-react-tailwind.md` or `references/adapters/vue-tailwind.md`

### Supabase Backend

- `references/layers/data.md`
- `references/layers/tenancy-isolation.md`
- `references/adapters/supabase-postgres-rls.md`

### AI Features

- `references/layers/api-integration.md`
- `references/adapters/openai.md`

### New Market Launch

- `references/layers/billing-subscription.md`
- `references/layers/compliance-privacy.md`
- `references/checklists/launch-gate.md`
- `templates/market-intake.template.md`
