# Technology Stack

> **Status:** Placeholder — Nothing in this document is a final decision. Every row below is a **candidate** under consideration. No technology choice takes effect until it is recorded as `Accepted` in an Architecture Decision Record (ADR) under [`docs/adr/`](adr/README.md).

## How to Read This Document

- **Candidate** — Being considered, not yet decided.
- **Pending ADR** — No ADR exists yet for this concern.
- References to a specific ADR number (e.g. `ADR-0003`) will be added here once that ADR reaches `Accepted` status.

## Runtime & Framework

| Layer | Candidate | ADR Reference |
|-------|-----------|----------------|
| Runtime | .NET (LTS release) | Pending ADR |
| Web Framework | ASP.NET Core | Pending ADR |
| Language | C# (latest LTS-compatible version) | Pending ADR |

## Authentication & Security

| Concern | Candidate(s) | ADR Reference |
|---------|--------------|----------------|
| Token Format | JSON Web Tokens (JWT) | Pending ADR |
| Token Signing | HMAC-SHA256 or RS256 | Pending ADR |
| Password Hashing | BCrypt or ASP.NET Core Identity | Pending ADR |
| Refresh Tokens | Opaque, server-side stored tokens | Pending ADR |

## Data & Persistence

| Concern | Candidate(s) | ADR Reference |
|---------|--------------|----------------|
| ORM | Entity Framework Core | Pending ADR |
| Database | PostgreSQL or SQL Server | Pending ADR |
| Caching | Not yet determined | Pending ADR |

## Testing

| Concern | Candidate(s) | ADR Reference |
|---------|--------------|----------------|
| Unit Tests | xUnit | Pending ADR |
| Mocking | Moq | Pending ADR |
| Integration Tests | WebApplicationFactory with Testcontainers | Pending ADR |

## Tooling

| Tool | Purpose | ADR Reference |
|------|---------|----------------|
| GitHub Actions | CI/CD pipelines | Pending ADR |
| dotnet CLI | Build, test, run | Pending ADR |
| EditorConfig | Code style enforcement | Pending ADR |

> All entries in this document are proposals only. The Architect persona may recommend a candidate, but only a human maintainer can accept an ADR and make a technology choice final. See [`docs/adr/README.md`](adr/README.md) for the ADR process.
