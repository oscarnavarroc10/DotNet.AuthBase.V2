# Project Rules

This file defines the non-negotiable rules for all contributors and AI agents working on DotNet.AuthBase.V2. Inject this file into your AI session context before starting any task.

---

## Spec-Driven Development Rules

1. **Specifications first.** Every feature must have an approved specification in `specs/` before implementation begins. There are no exceptions.

2. **No assumption allowed.** When information is intentionally deferred to a future ADR, Specification, or Plan, do not treat the absence of those details as an error.

3. **No unapproved scope.** Implement exactly what the specification describes. Do not add, remove, or modify behavior that is not explicitly specified.

4. **Decisions before code.** All significant architectural decisions must be recorded as ADRs in `docs/adr/` and reach `Accepted` status before related code is written.

5. **Traceability required.** Every code change must reference the specification or ADR that justifies it.

6. **AI agents recommend; humans approve.** No persona defined in `.ai/personas/` may set a specification to `Approved`, an ADR to `Accepted`, or merge a pull request. AI agents may only produce a recommendation; a human maintainer records the final decision.

## Security Rules

7. **No secrets in code.** Never commit API keys, passwords, connection strings, private keys, or any credential material to the repository.

8. **Security review mandatory.** Any code that handles authentication, authorization, token issuance, or user data must be reviewed by the Security Reviewer persona before merging.

9. **OWASP compliance.** All authentication flows must comply with OWASP Authentication and Session Management guidelines.

## Quality Rules

10. **Tests are mandatory.** No feature is complete without automated tests. The minimum coverage target is 80%.

11. **Tests must not be modified to pass.** If a test is failing, fix the production code. Do not delete, disable, or weaken tests.

12. **No debug code.** Do not commit console.log, Debug.WriteLine, or any debugging output to production code.

## Documentation Rules

13. **Keep documentation current.** When implementation diverges from documented behavior, update the documentation in the same pull request.

14. **ADRs are permanent.** Do not delete ADRs. If a decision is reversed, mark the original ADR as `Superseded` and create a new one.

## Pull Request Review Rules

15. During pull request reviews, prioritize contradictions, ambiguities, and violations of existing ADRs or Specifications.

16. Review ADRs as architectural decision records, not implementation documents. Focus on decision quality, consistency, consequences, and trade-offs. Do not request implementation details unless they contradict an accepted ADR.

17. Do not request implementation details, algorithms, frameworks, or libraries in Specifications. Those belong in ADRs or implementation Plans.

18. When implementation details are intentionally deferred, recommend creating or updating an ADR or Plan instead of expanding the current document.

19. Do not suggest splitting documents unless the repository convention explicitly requires it.

20. Prefer identifying inconsistencies over requesting additional detail.

21. During reviews, evaluate each document according to its responsibility. Do not request information that belongs in another document type. Missing details that are explicitly deferred to future ADRs, Specifications, or Plans must not be treated as defects.

## Review Philosophy

This repository follows Spec-Driven Development (SDD).

Each document has a specific responsibility:

- Vision defines project goals.
- ADRs define architectural decisions.
- Specifications define product behavior.
- Plans define implementation strategy.
- Tasks define implementation work.

During reviews, evaluate each document according to its responsibility. Do not request information that belongs in another document type.