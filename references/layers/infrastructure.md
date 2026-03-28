# Infrastructure Layer

## Scope

Infrastructure provides the deployment, environment, data, and release boundaries required by the framework.

## Core Rules

- Separate environments clearly and avoid leaking secrets into client bundles.
- Use versioned, reviewable migrations for schema changes.
- Make region and residency topology explicit.
- Keep release controls region-aware when a change can affect locale, market, or residency behavior.
- Support canary or staged rollout for globalization-affecting changes.
- Ensure backup, recovery, and failover plans respect tenancy and residency commitments.
- Distinguish delivery region from storage region from processing region.

## Required Artifacts

- environment and secret policy
- region topology map
- migration discipline
- release and rollback strategy

## Review Questions

- Can a deployment change break one locale or region without being detected?
- Are migrations safe for live systems with large localized or regulated datasets?
- Do failover plans violate stated residency expectations?
