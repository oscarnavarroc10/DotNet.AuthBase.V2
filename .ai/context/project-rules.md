# Project Rules

This file defines the non-negotiable rules for all contributors and AI agents working on DotNet.AuthBase.V2. Inject this file into your AI session context before starting any task.

---

## Spec-Driven Development Rules

1. **Specifications first.** Every feature must have an approved specification in `specs/` before implementation begins. There are no exceptions.

2. **No assumption allowed.** If a requirement is ambiguous, unclear, or missing, ask a clarifying question. Do not invent or assume missing details.

3. **No unapproved scope.** Implement exactly what the specification describes. Do not add, remove, or modify behavior that is not explicitly specified.

4. **Decisions before code.** All significant architectural decisions must be recorded as ADRs in `docs/decisions/` and reach `Accepted` status before related code is written.

5. **Traceability required.** Every code change must reference the specification or ADR that justifies it.

## Security Rules

6. **No secrets in code.** Never commit API keys, passwords, connection strings, private keys, or any credential material to the repository.

7. **Security review mandatory.** Any code that handles authentication, authorization, token issuance, or user data must be reviewed by the Security Reviewer persona before merging.

8. **OWASP compliance.** All authentication flows must comply with OWASP Authentication and Session Management guidelines.

## Quality Rules

9. **Tests are mandatory.** No feature is complete without automated tests. The minimum coverage target is 80%.

10. **Tests must not be modified to pass.** If a test is failing, fix the production code. Do not delete, disable, or weaken tests.

11. **No debug code.** Do not commit console.log, Debug.WriteLine, or any debugging output to production code.

## Documentation Rules

12. **Keep documentation current.** When implementation diverges from documented behavior, update the documentation in the same pull request.

13. **ADRs are permanent.** Do not delete ADRs. If a decision is reversed, mark the original ADR as `Superseded` and create a new one.
