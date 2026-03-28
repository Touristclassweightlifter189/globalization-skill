# Auth & Security Layer

## Scope

This layer covers authentication, authorization, abuse controls, secret handling, and region-aware security boundaries.

## Core Rules

- Use modern auth flows such as OIDC and PKCE where applicable.
- Apply least privilege to tokens, service accounts, and claims.
- Keep PII out of JWTs unless strictly necessary.
- Authorization decisions should depend on immutable claims or trusted server state.
- Model region or residency boundaries as security boundaries when required.
- Apply rate limiting and abuse controls to public or paid endpoints.
- Separate user-scoped access from service-role access.
- Audit cross-tenant and cross-region privileged operations.

## Required Artifacts

- auth-flow diagram
- claims and role model
- rate-limit policy
- privileged-path audit policy

## Review Questions

- Could a mutable client-side field influence authorization?
- Are public AI or payment endpoints protected against replay and abuse?
- Is privileged cross-region processing justified and logged?
