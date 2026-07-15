# Glossary

This glossary defines terms used throughout the DotNet.AuthBase.V2 project. All contributors and AI agents should use these terms consistently.

> **Status:** Placeholder — Terms will be added and refined as specifications are written.

---

## Authentication & Security Terms

**Access Token**
A short-lived JWT issued upon successful authentication, used to authorize API requests.

**Refresh Token**
An opaque, long-lived token used to obtain a new access token when the current one expires. Refresh tokens are rotated on each use and revoked on logout.

**JWT (JSON Web Token)**
An open standard (RFC 7519) for securely transmitting information between parties as a JSON object, signed using HMAC or RSA.

**Token Rotation**
The practice of issuing a new refresh token each time an existing one is used, and invalidating the old token. This limits the window of opportunity if a token is compromised.

**Token Revocation**
The act of invalidating a refresh token before its natural expiry, typically on logout or when a compromise is detected.

**OWASP**
The Open Web Application Security Project, a nonprofit that publishes widely used security standards and guidelines.

---

## Development Process Terms

**Spec-Driven Development (SDD)**
A development methodology in which a written, approved specification is a prerequisite for any implementation work. Specifications are the source of truth for product behavior.

**Architecture Decision Record (ADR)**
A short document that captures a significant architectural decision, its context, and its consequences. Stored in `docs/decisions/`.

**Specification**
A document in `specs/` that describes the expected behavior, requirements, and acceptance criteria for a feature. Must be approved before implementation begins.

**Acceptance Criteria**
A set of conditions that a feature must satisfy to be considered complete and correct.

**Persona**
A role definition for an AI agent (e.g., Product Owner, Architect). Personas define the agent's responsibilities and constraints for a specific type of task.

---

## Project-Specific Terms

**AuthBase**
The authentication foundation provided by this project, encompassing token issuance, validation, refresh, and revocation.

**Core Layer**
The `DotNet.AuthBase.Core` project, containing domain models, interfaces, and abstractions with no external dependencies.

**Infrastructure Layer**
The `DotNet.AuthBase.Infrastructure` project, containing data access, token storage, and external integrations.

**API Layer**
The `DotNet.AuthBase.Api` project, containing ASP.NET Core endpoints, middleware, and HTTP concerns.
