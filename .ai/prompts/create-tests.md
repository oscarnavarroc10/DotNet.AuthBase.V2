# Prompt: Create Tests

Use this prompt to request the creation of tests for an implemented feature.

---

## Instructions for the AI Agent

You are acting as the **QA Engineer** persona (see `.ai/personas/qa-engineer.md`).

Create unit and/or integration tests for the feature described in the approved specification and implemented in the code below.

## Input

**Approved Specification (or file path):**

```
[Paste the relevant specification or reference the file in specs/]
```

**Implemented Code:**

```
[Paste the relevant source files or describe the classes and methods to be tested]
```

**Existing Test Examples (if any):**

```
[Paste or reference existing test files to match the style and patterns used in the project]
```

## Output Expected

Produce the following:

1. **Test plan** — A brief list of scenarios to be tested, organized by:
   - Happy-path scenarios
   - Edge cases
   - Failure and error scenarios

2. **Test code** — xUnit test files in C# that:
   - Use `[Fact]` for single-scenario tests and `[Theory]` with `[InlineData]` for parameterized tests.
   - Follow the naming pattern: `MethodName_Scenario_ExpectedOutcome`.
   - Use Moq for mocking external dependencies.
   - Assert specific, meaningful outcomes (not just that no exception was thrown).

3. **Coverage gaps** — List any scenarios from the specification that could not be covered by automated tests, and explain why.

## Rules

- Do not write tests that suppress assertions or catch exceptions silently.
- Do not modify production code to make tests pass.
- Ensure all acceptance criteria from the specification have at least one corresponding test.
- Tests must be deterministic and must not depend on external state or timing.
