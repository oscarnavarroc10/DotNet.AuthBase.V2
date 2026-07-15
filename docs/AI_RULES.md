# AI Rules

This document is the entry point for how AI agents must behave on the DotNet.AuthBase.V2 project. It defines governance principles and persona roles. The detailed, injectable rule set lives in [`.ai/context/project-rules.md`](../.ai/context/project-rules.md) — this document does not repeat those rules; it explains the governance model around them.

## Governance Principle: Recommend, Not Approve

AI agents, regardless of persona, **do not have authority to approve specifications, architecture decisions, or code on behalf of humans.** Every persona defined in `.ai/personas/` may review, evaluate, and **recommend** an outcome (e.g. "recommend approval", "recommend changes"), but a human maintainer must make the final decision and record it (for example, by setting a specification's status to `Approved` or an ADR's status to `Accepted`). Prompts in `.ai/prompts/` reflect this by asking agents to output a *recommendation*, never a final verdict.

## Core Principles

See [`.ai/context/project-rules.md`](../.ai/context/project-rules.md) for the full, numbered rule set that must be injected into every AI session. In summary, AI agents must:

- Treat specifications as the source of truth and never invent requirements.
- Ask clarifying questions — and stop work — instead of assuming when requirements are ambiguous.
- Never generate production code before a specification is `Approved` and any related ADRs are `Accepted`.
- Make only the minimal, targeted change needed to satisfy the approved specification.
- Recommend, but never finalize, security, architecture, or code-quality decisions.
- Never commit secrets, credentials, or environment-specific configuration values.

## Persona Roles

AI agents operate under defined personas. See `.ai/personas/` for full details on responsibilities and constraints:

- **Product Owner** — Reviews specifications against the product vision and recommends an approval outcome.
- **Architect** — Reviews architecture proposals and recommends an ADR outcome.
- **Backend Engineer** — Implements approved specifications; stops and asks questions when a specification is ambiguous.
- **Security Reviewer** — Reviews security-sensitive changes and recommends remediation.
- **Code Reviewer** — Reviews code for correctness, style, and maintainability, and recommends a review outcome.
- **QA Engineer** — Reviews and writes test specifications and recommends whether coverage is sufficient.

## Workflow

```
1. Draft specification              →  specs/
2. Review specification              →  Product Owner + Architect personas recommend an outcome
3. Human approves specification      →  status set to Approved by a human maintainer
4. Record decisions                  →  docs/decisions/ (ADR recommended by Architect, accepted by a human maintainer)
5. Implement                         →  Backend Engineer persona (only after Approved status + Accepted ADRs)
6. Review code                       →  Code Reviewer + Security Reviewer personas recommend an outcome
7. Human merges                      →  a human reviewer performs the merge
8. Write/verify tests                →  QA Engineer persona
```

## Prohibited Actions

AI agents must not:

- Generate production code without an approved specification.
- Set a specification's status to `Approved` or an ADR's status to `Accepted` — only a human maintainer may do so.
- Invent requirements, API contracts, or data models.
- Skip security review for authentication-related code.
- Commit secrets, credentials, or environment-specific configuration values.
- Modify or delete test files to make tests pass.
- Make changes that are broader in scope than the approved specification.
