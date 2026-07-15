# Technology Stack

> **Status:** Placeholder — Technology choices are preliminary and will be finalized through Architecture Decision Records before implementation begins.

## Runtime & Framework

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| Runtime | .NET 8 (LTS) | Long-term support, performance, cross-platform |
| Web Framework | ASP.NET Core 8 | Industry-standard for .NET APIs |
| Language | C# 12 | Latest stable language features |

## Authentication & Security

| Concern | Technology | Rationale |
|---------|-----------|-----------|
| Token Format | JSON Web Tokens (JWT) | Stateless, widely supported |
| Token Signing | HMAC-SHA256 / RS256 (TBD) | To be decided via ADR |
| Password Hashing | BCrypt / ASP.NET Core Identity (TBD) | To be decided via ADR |
| Refresh Tokens | Opaque tokens stored server-side | Security best practice |

## Data & Persistence

| Concern | Technology | Rationale |
|---------|-----------|-----------|
| ORM | Entity Framework Core 8 | Native .NET ORM, migrations support |
| Database | PostgreSQL (default) / SQL Server (optional) | To be decided via ADR |
| Caching | Not yet determined | To be decided via ADR |

## Testing

| Concern | Technology | Rationale |
|---------|-----------|-----------|
| Unit Tests | xUnit | Standard .NET test framework |
| Mocking | Moq | Widely used, mature library |
| Integration Tests | WebApplicationFactory + Testcontainers (TBD) | In-process API testing |

## Tooling

| Tool | Purpose |
|------|---------|
| GitHub Actions | CI/CD pipelines |
| dotnet CLI | Build, test, run |
| EditorConfig | Code style enforcement |

> All technology choices are subject to change until formally recorded in an ADR.
