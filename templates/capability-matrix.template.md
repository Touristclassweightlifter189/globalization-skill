# Capability Matrix Template

## Purpose

Track supported combinations before implementation assumes they exist.

## Dimensions

- market country
- jurisdiction
- seller role
- payment method
- currency
- invoice format
- provider
- provider region
- feature
- channel

## Matrix Row Template

| Market | Jurisdiction | Seller Role | Provider | Feature | Currency | Payment Method | Invoice Format | Supported | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |  |  |  |  |

## Example

| Market | Jurisdiction | Seller Role | Provider | Feature | Currency | Payment Method | Invoice Format | Supported | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SG | SG | direct_merchant | Stripe | subscription_checkout | SGD | card | pdf | yes | standard v1 launch path |
| HK | HK | direct_merchant | Stripe | subscription_checkout | HKD | card | pdf | yes | no residency claim |
| IN | IN | direct_merchant | Stripe | recurring_subscription | INR | card | regulated | no | mandate rules need dedicated adapter work |
