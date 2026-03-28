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

## Invoice Lineage Example

```sql
create table billing_invoices (
  id uuid primary key,
  tenant_id uuid not null,
  external_invoice_id text,
  seller_role text not null,
  currency_code text not null,
  amount_minor bigint not null,
  status text not null,
  replaced_by_invoice_id uuid references billing_invoices(id),
  cancellation_reason text,
  tax_evidence jsonb not null default '{}'::jsonb,
  created_at timestamptz not null default now()
);
```

## Operational Rules

- Handle payment gateway state asynchronously.
- Use explicit enum states for subscription and mandate lifecycle.
- Separate entitlement change from payment event receipt.
- Distinguish presentment, settlement, and reporting currency where needed.

## Stripe Webhook Example

```ts
export async function handleStripeWebhook(req: Request, stripe: any) {
  const body = await req.text()
  const signature = req.headers.get('stripe-signature') ?? ''

  const event = stripe.webhooks.constructEvent(
    body,
    signature,
    process.env.STRIPE_WEBHOOK_SECRET
  )

  if (event.type === 'invoice.paid') {
    const invoice = event.data.object

    await upsertInvoice({
      externalInvoiceId: invoice.id,
      tenantId: invoice.metadata.tenant_id,
      sellerRole: invoice.metadata.seller_role,
      currencyCode: invoice.currency.toUpperCase(),
      amountMinor: invoice.amount_paid,
      status: 'paid',
    })
  }

  return new Response('ok')
}
```

Process entitlement changes after persistence, not inline before webhook verification. Keep provider IDs and internal lineage linked.

## Review Checklist

- Does the product know who is legally selling?
- Are invoice and tax records audit-ready for the target market?
- Can unsupported payment methods or currencies fail clearly before checkout?
