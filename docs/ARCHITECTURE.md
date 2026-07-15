# Architecture

> **Status:** Placeholder — Architecture decisions will be documented here before implementation begins. No production code has been written yet.

## Overview

This document describes a **proposed** high-level architecture for DotNet.AuthBase.V2. Nothing here is final. Every structural choice, layer boundary, or flow described below is a candidate for discussion and must be recorded as an Architecture Decision Record (ADR) in `docs/decisions/` — and reach `Accepted` status — before implementation begins.

## Proposed Component Structure

> The layout below is a starting proposal, not a finalized design. It will be superseded by whatever structure the corresponding ADR(s) accept.

```
DotNet.AuthBase.V2 (ASP.NET Core solution)
├── DotNet.AuthBase.Core          # Domain models, interfaces, abstractions
├── DotNet.AuthBase.Infrastructure # Data access, token storage, external integrations
├── DotNet.AuthBase.Api            # HTTP endpoints and middleware
└── DotNet.AuthBase.Tests          # Unit and integration tests
```

## Guiding Principles (Proposed)

- **Separation of Concerns** — Business logic, infrastructure, and API layers should remain independent.
- **Security by Default** — Authentication flows should follow OWASP best practices.
- **Testability** — Components should be designed for unit and integration testing.
- **Spec-Driven** — No component is implemented without an approved specification.

These principles are recommendations from the Architect persona. They become binding only once captured in an `Accepted` ADR.

## Authentication Flow (Proposed Outline)

> The following is a preliminary, non-binding outline. Each flow will be fully specified in `specs/` and its architectural implications recorded in an ADR before implementation.

1. User submits credentials.
2. Credentials are validated against a secure store.
3. A short-lived JWT access token and a refresh token are issued.
4. The access token is used to authenticate subsequent requests.
5. The refresh token is used to obtain a new access token when the current one expires.
6. Refresh tokens are rotated on each use and revoked on logout.

## Architecture Decision Records

All significant decisions are recorded in [`docs/decisions/`](decisions/README.md).
