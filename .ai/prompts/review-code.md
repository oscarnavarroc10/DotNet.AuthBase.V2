# Prompt: Review Code

Use this prompt to request a code review for a pull request or code change.

---

## Instructions for the AI Agent

You are acting as the **Code Reviewer** persona (see `.ai/personas/code-reviewer.md`).

Review the code changes provided below. Evaluate them for correctness, alignment with the approved specification, and adherence to the coding guidelines.

## Input

**Approved Specification (or file path):**

```
[Paste the relevant specification or reference the file in specs/]
```

**Code Changes:**

```
[Paste the diff, file contents, or describe the changed files]
```

**Additional Context (optional):**

```
[Any relevant background, constraints, or decisions]
```

## Output Expected

Provide a structured review with the following sections:

### Specification Alignment
- Does the code implement what the specification requires?
- Are all acceptance criteria met?
- Is anything implemented that is not in the specification?

### Correctness
- Are there any bugs, logic errors, or unhandled edge cases?
- Is error handling appropriate and consistent?

### Code Quality
- Does the code follow the guidelines in `.ai/context/coding-guidelines.md`?
- Is the code readable and maintainable?
- Are there any unnecessary dependencies or complexity?

### Test Coverage
- Are the changes adequately covered by tests?
- Are edge cases and failure scenarios tested?

### Security
- Are there any security concerns that require the Security Reviewer's attention?

### Recommendation

State a recommendation for the human reviewer, who retains final merge authority:

- `Recommend Approval` — Appears ready to merge.
- `Recommend Approval with Minor Comments` — May be merged after addressing minor issues, at the human reviewer's discretion.
- `Recommend Changes` — List blocking issues that must be resolved before it can be considered ready.

## Rules

- Do not present a recommendation as if it were a merge decision; only a human reviewer may approve and merge.
- Do not recommend approval for code with known bugs or unhandled failure scenarios.
- Flag any security concerns for the Security Reviewer.
