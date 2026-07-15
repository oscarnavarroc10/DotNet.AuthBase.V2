# Specifications

This directory contains feature specifications for DotNet.AuthBase.V2.

## Purpose

Specifications are the **source of truth** for product behavior. No production code may be written for a feature until its specification has been reviewed and approved.

## Structure

Each specification lives in its own subdirectory and follows a consistent format:

```
specs/
└── <feature-name>/
    ├── README.md        # Specification summary and status
    ├── requirements.md  # Functional and non-functional requirements
    └── acceptance.md    # Acceptance criteria and test scenarios
```

## Specification Status

| Status | Meaning |
|--------|---------|
| `Draft` | Being written, not yet ready for review |
| `In Review` | Submitted for review |
| `Approved` | Approved for implementation |
| `Implemented` | Code has been written and tested |
| `Rejected` | Will not be implemented |

## Process

1. Create a new subdirectory under `specs/` for the feature.
2. Write a draft specification following the format above.
3. Request review using the prompt in `.ai/prompts/review-specification.md`.
4. Incorporate feedback and update the status to `Approved`.
5. Implementation may begin only after approval.

## Index

> No specifications have been written yet. This directory will be populated as features are defined.
