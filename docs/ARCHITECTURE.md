# Architecture

> **Status:** Placeholder — Architecture decisions will be documented here before implementation begins. No production code has been written yet.

## Overview

This document describes the planned high-level architecture for DotNet.AuthBase.V2. All architectural decisions must be recorded as Architecture Decision Records (ADRs) in `docs/decisions/` before implementation begins.

## Planned Component Structure

```
DotNet.AuthBase.V2 (ASP.NET Core solution)
├── DotNet.AuthBase.Core          # Domain models, interfaces, abstractions
├── DotNet.AuthBase.Infrastructure # Data access, token storage, external integrations
├── DotNet.AuthBase.Api            # HTTP endpoints and middleware
└── DotNet.AuthBase.Tests          # Unit and integration tests
```

## Guiding Principles

- **Separation of Concerns** — Business logic, infrastructure, and API layers are kept independent.
- **Security by Default** — All authentication flows follow OWASP best practices.
- **Testability** — All components are designed for unit and integration testing.
- **Spec-Driven** — No component is implemented without an approved specification.

## Authentication Flow (Planned)

> The following is a preliminary outline. Each flow will be fully specified in `specs/` before implementation.

1. User submits credentials.
2. Credentials are validated against a secure store.
3. A short-lived JWT access token and a refresh token are issued.
4. The access token is used to authenticate subsequent requests.
5. The refresh token is used to obtain a new access token when the current one expires.
6. Refresh tokens are rotated on each use and revoked on logout.

## Architecture Decision Records

All significant decisions are recorded in [`docs/decisions/`](decisions/README.md).
