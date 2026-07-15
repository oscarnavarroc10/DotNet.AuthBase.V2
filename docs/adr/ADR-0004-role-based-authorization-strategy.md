# ADR-0004: Role-Based Authorization Strategy

- **Status:** Proposed
- **Date:** 2026-07-15
- **Related Specification:** SPEC-0001 Authentication Foundation
- **Related Decision:** ADR-0002 Token and Session Strategy

## Context

DotNet.AuthBase.V2 must support authorization based on user roles.

The first version needs a model that:

- Supports multiple roles per user.
- Prevents clients from assigning roles to themselves.
- Supports protected ASP.NET Core operations.
- Includes role information in newly issued access tokens.
- Remains simple enough for a reusable authentication foundation.
- Can evolve toward more granular authorization later without introducing permissions prematurely.

## Decision

The initial authorization model will use role-based authorization.

Users may have one or more roles.

Role definitions and user-role assignments will be controlled by the server.

The initial version will not implement a granular permission model.

## Role Assignment

Public registration will assign a server-controlled default role.

Clients will not be allowed to:

- Select their initial role.
- Assign roles during registration.
- Modify their own role assignments.
- Submit privileged role claims that are trusted by the server.

Role assignments may only be changed through an authorized administrative operation.

Administrative authorization must be evaluated using server-issued identity information, not values supplied by the requesting client.

## Access Tokens

New access tokens will include the authenticated user's current roles as role claims.

Protected operations may require:

- An authenticated user.
- One required role.
- Any role from an allowed set.

Access will be denied when the authenticated user does not satisfy the required role rules.

Role claims contained in an already-issued access token may remain unchanged until that token expires.

Role changes will apply immediately to:

- Future authentication sessions.
- Future session refresh operations.
- Newly issued access tokens.

Immediate invalidation of existing access tokens after a role change is not part of the initial strategy.

## Application Boundaries

Authorization requirements will be declared at the API or application boundary.

Domain entities will not depend on:

- ASP.NET Core authorization attributes.
- HTTP concepts.
- JWT claims.
- Framework-specific authorization types.

Application use cases may receive an abstract representation of the authenticated user and their assigned roles when authorization is required inside the application boundary.

Infrastructure and API components will translate authenticated token claims into that application representation.

## Default Roles

The system will support a configurable default role for newly registered users.

The concrete initial role names will be determined during implementation planning or deployment configuration.

No role name will be treated as privileged solely because it was supplied by a client.

## Consequences

### Positive

- Provides a simple authorization model suitable for the initial version.
- Works directly with ASP.NET Core authorization mechanisms.
- Supports multiple roles per user.
- Prevents role assignment during public registration.
- Keeps framework-specific authorization details outside the Domain layer.
- Allows permission-based authorization to be introduced later through a separate decision.

### Negative

- Role claims may be stale until an existing access token expires.
- Roles can become too broad as authorization requirements grow.
- Complex authorization rules may not map cleanly to roles.
- Immediate role revocation would require additional access-token state validation.

## Alternatives Considered

### Permission-Based Authorization

Deferred because the initial specification only requires roles. Introducing permissions now would expand the domain model and administrative workflows without an approved requirement.

### Authorization Stored Only in the Database

Rejected for normal access-token validation because it would require a database lookup for every protected request and conflict with ADR-0002.

### Client-Controlled Role Selection

Rejected because it would allow privilege escalation.

### Immediate Access-Token Revocation After Role Changes

Deferred because it would require a token denylist, token-version lookup, or another server-side check during protected requests.

## Deferred Decisions

The following details will be defined during implementation planning or future specifications:

- Initial role names.
- Default role configuration.
- Initial administrator provisioning.
- Administrative role-management endpoints.
- Role persistence schema.
- Role-name normalization.
- Hierarchical roles.
- Permission-based authorization.
- Policy-based business rules beyond basic role checks.