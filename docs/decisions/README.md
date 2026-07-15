# Architecture Decision Records

This directory contains Architecture Decision Records (ADRs) for DotNet.AuthBase.V2.

## What is an ADR?

An Architecture Decision Record documents a significant architectural decision made during the project. Each record captures the context, the decision, and its consequences, so that future contributors understand why the system is built the way it is.

## Status Values

| Status | Meaning |
|--------|---------|
| `Proposed` | Under review, not yet approved |
| `Accepted` | Approved and in effect |
| `Deprecated` | No longer in effect |
| `Superseded` | Replaced by another ADR |

## Naming Convention

ADR files are named using the following pattern:

```
NNNN-short-title.md
```

Example: `0001-use-jwt-for-authentication.md`

## Process

1. Create a new ADR file in this directory following the naming convention.
2. Set status to `Proposed`.
3. Request a recommendation from the Architect persona (see `.ai/personas/architect.md`). The persona may recommend acceptance, revision, or rejection, but cannot change the status itself.
4. A human maintainer reviews the recommendation and, if in agreement, updates the status to `Accepted`.
5. No implementation may begin until the related ADR is `Accepted` by a human maintainer.

## Index

> No decisions have been recorded yet. ADRs will be added here as the project progresses.
