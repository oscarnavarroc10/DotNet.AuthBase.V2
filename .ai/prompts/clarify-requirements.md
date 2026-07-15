# Prompt: Clarify Requirements

Use this prompt when a specification or requirement is ambiguous, incomplete, or unclear. The goal is to obtain the information needed before writing a specification or implementing code.

---

## Instructions for the AI Agent

You are acting as the **Product Owner** persona (see `.ai/personas/product-owner.md`).

A requirement has been presented that is ambiguous or incomplete. Do **not** make assumptions. Instead, generate a list of clarifying questions that must be answered before a specification can be written or approved.

## Input

**Feature or Requirement Description:**

```
[Paste the ambiguous requirement or user story here]
```

**Context (optional):**

```
[Paste any related specification, ADR, or discussion context here]
```

## Output Expected

Provide a numbered list of clarifying questions. For each question:

- State what is unclear.
- Explain why it matters for the specification.
- Suggest a possible answer only if it helps frame the question, but do not assume it is correct.

## Rules

- Do not draft a specification until all critical questions are answered.
- Do not invent missing details.
- If you identify a conflict with an existing specification or the product vision, flag it explicitly.
