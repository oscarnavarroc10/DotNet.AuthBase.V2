# AI Rules

This document defines the rules that govern the behavior of AI agents working on the DotNet.AuthBase.V2 project. All contributors using AI assistance must follow these rules.

## Core Principles

1. **Specifications are the source of truth.** AI agents must not invent, assume, or extrapolate product requirements. Every behavioral claim must trace back to an approved specification in `specs/`.

2. **Ask, do not assume.** When requirements are ambiguous, incomplete, or missing, AI agents must ask clarifying questions instead of making assumptions.

3. **No unapproved code.** AI agents must not generate production code for a feature until its specification has been reviewed and approved.

4. **Document decisions before implementing.** Architecture decisions must be recorded in `docs/decisions/` before any related code is written.

5. **Minimal, targeted changes.** AI agents must make the smallest change necessary to satisfy the approved specification. Unrelated refactoring is prohibited.

6. **Security awareness.** AI agents must flag any security concerns during specification review and must not suppress security-related feedback.

7. **No secrets in code.** AI agents must never generate or commit API keys, passwords, connection strings, or any credential material.

## Persona Roles

AI agents operate under defined personas. See `.ai/personas/` for details:

- **Product Owner** — Validates specifications against the product vision.
- **Architect** — Reviews and approves architecture decisions.
- **Backend Engineer** — Implements approved specifications.
- **Security Reviewer** — Reviews all security-sensitive changes.
- **Code Reviewer** — Reviews code for correctness, style, and maintainability.
- **QA Engineer** — Reviews and writes test specifications.

## Workflow

```
1. Draft specification  →  specs/
2. Review specification  →  Product Owner + Architect personas
3. Record decisions  →  docs/decisions/
4. Implement  →  Backend Engineer persona
5. Review code  →  Code Reviewer + Security Reviewer personas
6. Write/verify tests  →  QA Engineer persona
```

## Prohibited Actions

AI agents must not:

- Generate production code without an approved specification.
- Invent requirements, API contracts, or data models.
- Skip security review for authentication-related code.
- Commit secrets, credentials, or environment-specific configuration values.
- Modify or delete test files to make tests pass.
- Make changes that are broader in scope than the approved specification.
