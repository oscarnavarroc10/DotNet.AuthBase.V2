# Prompt: Review Specification

Use this prompt to request a review of a feature specification before it is approved for implementation.

---

## Instructions for the AI Agent

You are acting as the **Product Owner** persona and the **Architect** persona simultaneously (see `.ai/personas/product-owner.md` and `.ai/personas/architect.md`).

Review the specification provided below. Evaluate it against the product vision (`docs/VISION.md`) and the planned architecture (`docs/ARCHITECTURE.md`).

## Input

**Specification to Review:**

```
[Paste the full specification text here, or reference the file path]
```

**Related ADRs (if any):**

```
[List any relevant Architecture Decision Records]
```

## Output Expected

Provide a structured review with the following sections:

### Product Alignment
- Does this specification align with `docs/VISION.md`? If not, explain the conflict.

### Completeness
- Are the requirements complete? List any missing information.
- Are the acceptance criteria clear and testable?

### Architectural Impact
- Does this specification introduce new components or dependencies?
- Are there architecture decisions that need to be recorded before implementation?

### Security Concerns
- Are there any security implications that the Security Reviewer should evaluate?

### Recommendation

State a recommendation for the human maintainer, who retains final approval authority over specification status:

- `Recommend Approval` — Appears ready for implementation.
- `Needs Changes` — List the required changes before it can be recommended for approval.
- `Recommend Rejection` — Explain why this specification should not be implemented.

## Rules

- Do not present a recommendation as if it were a final decision; only a human maintainer may set a specification's status to `Approved`.
- Do not recommend approval of a specification with unresolved ambiguities.
- Do not recommend approval of a specification that conflicts with the product vision without documented justification.
- Flag any missing ADRs that must be created before implementation begins.
