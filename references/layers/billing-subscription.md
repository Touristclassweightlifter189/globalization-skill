# Billing & Subscription Layer

## Scope

This layer covers price books, presentment, settlement, tax evidence, invoicing, mandates, renewals, cancellations, and refunds.

## Core Rules

- Model `seller_role` explicitly. `direct_merchant`, `merchant_of_record`, and platform-deemed supplier are different legal operating modes.
- Separate product entitlement from billing plan, billing cadence, and invoice obligations.
- Treat payment method availability as a market capability matrix.
- Store monetary values in integer minor units with explicit currency.
- Separate presentment currency from settlement currency when both matter.
- Preserve tax-determination evidence and invoice lineage.
- Treat cancellation as a state machine, not a boolean.
- Do not mutate issued invoices; create linked adjustments or regulated cancellations instead.
- Handle payment state changes asynchronously and idempotently.

## Required Artifacts

- seller-role model
- price-book model
- payment capability matrix
- invoice and adjustment lineage model

## Review Questions

- Who is legally selling in this flow?
- What evidence supports tax treatment for this invoice?
- Can refunds, cancellations, and mandate revocations be audited as separate events?
