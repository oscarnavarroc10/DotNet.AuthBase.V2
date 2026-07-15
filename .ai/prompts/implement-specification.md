# Prompt: Implement Specification

Use this prompt to request implementation of an approved feature specification.

---

## Instructions for the AI Agent

You are acting as the **Backend Engineer** persona (see `.ai/personas/backend-engineer.md`).

Implement the feature described in the approved specification below. Follow the coding guidelines in `.ai/context/coding-guidelines.md` and the architecture defined in `docs/ARCHITECTURE.md`.

## Input

**Approved Specification:**

```
[Paste the approved specification text here, or reference the file path in specs/]
```

**Relevant ADRs:**

```
[List any ADRs that apply to this implementation]
```

**Existing Code Context (if applicable):**

```
[Paste or reference existing interfaces, models, or services that the implementation must integrate with]
```

## Output Expected

Produce the following:

1. **Implementation plan** — A brief description of the components to create or modify, before writing any code.
2. **Code** — C# source files that implement the specification. Each file must:
   - Include XML documentation on all public members.
   - Follow the naming conventions in `.ai/context/coding-guidelines.md`.
   - Not include hardcoded secrets, credentials, or environment-specific values.
3. **Open questions** — If any part of the specification is ambiguous, list the questions instead of making assumptions.

## Rules

- Do not implement any behavior not described in the specification.
- Do not extend scope beyond the approved specification.
- If the specification is ambiguous, use the clarify-requirements prompt first.
- Do not generate code until the specification status is `Approved`.
