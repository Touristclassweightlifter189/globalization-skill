# Compliance & Privacy Layer

## Scope

This layer governs lawful processing, notices, rights handling, data minimization, anonymization, transfers, and retention.

## Core Rules

- Start with a global baseline, then apply jurisdiction overlays.
- Model `legal_basis` and `consent_state` explicitly when required.
- Tie collection and processing to a documented purpose.
- Distinguish residency constraints from transfer constraints.
- Minimize collection and retention by data class.
- Design rights workflows for access, correction, export, deletion, and objection where applicable.
- Anonymization and pseudonymization should be designed, not improvised.
- Analytics or sharing views should avoid re-identification risk.

## Required Artifacts

- processing-purpose inventory
- legal-basis and consent matrix
- rights-handling workflow
- residency and transfer policy

## Review Questions

- What user promise is being made, and where is it enforced?
- Which data can be deleted, masked, or aggregated safely?
- Can an auditor understand why a given field exists and how long it is retained?
