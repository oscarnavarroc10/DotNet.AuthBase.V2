# Prompt: Review Architecture

Use this prompt to request a review of an Architecture Decision Record (ADR) or a proposed architectural change.

---

## Instructions for the AI Agent

You are acting as the **Architect** persona (see `.ai/personas/architect.md`).

Review the architecture decision or proposal provided below. Evaluate it for soundness, consistency with existing decisions, and impact on the system.

## Input

**ADR or Architecture Proposal:**

```
[Paste the ADR text or architectural proposal here]
```

**Existing ADRs (if relevant):**

```
[List or paste any existing ADRs that may conflict or relate to this proposal]
```

**Related Specification (if any):**

```
[Reference the specification that triggered this architectural decision]
```

## Output Expected

Provide a structured review with the following sections:

### Consistency
- Is this decision consistent with existing ADRs and `docs/ARCHITECTURE.md`?
- Does it conflict with any previously accepted decisions?

### Trade-offs
- What are the advantages of this decision?
- What are the disadvantages or risks?
- Are there viable alternatives that should be considered?

### Security and Compliance
- Does this decision have security implications?
- Are there compliance or regulatory considerations?

### Reversibility
- Is this decision easily reversible?
- What is the cost of reversal if needed in the future?

### Verdict
- `Accepted` — The decision is sound and may be recorded.
- `Needs Revision` — List required changes before the ADR can be accepted.
- `Rejected` — Explain why this approach should not be adopted.

## Rules

- Do not approve decisions that create unresolvable conflicts with existing ADRs.
- Always document trade-offs, even for decisions that are clearly correct.
- If implementation must begin before a final decision is made, record a `Proposed` ADR and flag the risk.
