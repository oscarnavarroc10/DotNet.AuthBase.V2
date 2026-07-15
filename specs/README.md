# Specifications

This directory contains feature specifications for DotNet.AuthBase.V2.

## Purpose

Specifications are the **source of truth** for product behavior. No production code may be written for a feature until its specification has been reviewed and approved.

## Structure

Each specification lives in its own subdirectory and is defined in a single specification document:

```text
specs/
└── <feature-name>/
    └── spec.md
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
3. Request a recommendation using the prompt in `.ai/prompts/review-specification.md`. The AI reviewer may recommend approval, changes, or rejection, but cannot change the status itself.
4. Incorporate feedback. A human maintainer reviews the recommendation and, if in agreement, updates the status to `Approved`.
5. Implementation may begin only after a human maintainer sets the status to `Approved`.

## Index

| ID | Title | Status |
|----|-------|--------|
| SPEC-0001 | Authentication Foundation | In Review |