# Tests

This directory will contain the automated test suite for DotNet.AuthBase.V2.

> **Status:** Not yet implemented. This directory is a placeholder.
>
> This initial pull request contains documentation and repository structure only. No test code has been written.

## Planned Structure

```
tests/
├── DotNet.AuthBase.UnitTests/       # Unit tests for core logic
└── DotNet.AuthBase.IntegrationTests/ # Integration tests for API endpoints
```

## Testing Standards

- All production code must have unit tests before it can be considered complete.
- Integration tests must cover all authentication flows end-to-end.
- Tests must be written or reviewed by the QA Engineer persona (see `.ai/personas/qa-engineer.md`).
- Test coverage target: 80% or higher across all production code.

## Prerequisites for Test Implementation

Before any test code is added to this directory:

1. The corresponding production code in `src/` must exist.
2. The related specification in `specs/` must be in `Approved` status.

## Getting Started (Future)

Once tests are implemented, instructions for running the test suite will be added here.
