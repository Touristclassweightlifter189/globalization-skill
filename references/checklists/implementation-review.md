# Implementation Review Checklist

## Implementation Review Checklist

- Are translation keys stable and non-computed?
- Are dynamic strings built with interpolation rather than concatenation?
- Is `lang`, `dir`, and formatter state driven from one resolved locale contract?
- Are canonical IDs, status values, and timestamps preserved?
- Are governance-critical fields stored in typed columns or equivalent first-class fields?
- Is tenant scope enforced on every read, write, cache, and background path?
- Are auth decisions based on trusted claims?
- Are provider integrations idempotent, verified, and capability-aware?
- Are structured logs redacted and attributed with the right context?
- Are unsupported markets, currencies, locales, or regions rejected explicitly?
