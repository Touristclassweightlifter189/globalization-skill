# Billing Tax Adapter

## Purpose

Maps the billing layer into payment-provider, invoicing, and tax-sensitive implementation.

## Mapping Rules

- Model seller role explicitly and propagate it into invoice, refund, and tax logic.
- Maintain market capability matrices for payment methods, currencies, invoice format requirements, and tax evidence.
- Preserve immutable invoice lineage:
  - original invoice
  - adjustment or credit note
  - replacement or cancellation reference
- Keep tax evidence alongside the computed result, not only the final tax amount.
- Treat recurring payments, mandates, and cancellation rules as jurisdiction-sensitive workflows.

## Operational Rules

- Handle payment gateway state asynchronously.
- Use explicit enum states for subscription and mandate lifecycle.
- Separate entitlement change from payment event receipt.
- Distinguish presentment, settlement, and reporting currency where needed.

## Review Checklist

- Does the product know who is legally selling?
- Are invoice and tax records audit-ready for the target market?
- Can unsupported payment methods or currencies fail clearly before checkout?
