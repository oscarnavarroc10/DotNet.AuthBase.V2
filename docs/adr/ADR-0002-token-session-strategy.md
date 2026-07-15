# ADR-0002: Token and Session Strategy

- **Status:** Proposed
- **Date:** 2026-07-15
- **Related Specification:** SPEC-0001 Authentication Foundation

## Context

DotNet.AuthBase.V2 requires JWT-based authentication with support for secure session renewal, logout, token rotation, and revocation.

Access tokens must allow protected API requests to be validated without requiring a database lookup on every request.

At the same time, the system must retain control over long-lived sessions so that refresh tokens can expire, rotate, and be revoked.

This decision must support mobile and web clients without requiring the client to store or resend the user's password after authentication.

## Decision

### Access Tokens

Access tokens will be signed JSON Web Tokens.

They will:

- Have a short, configurable lifetime.
- Include only the claims required for authentication and role-based authorization.
- Be validated using signature, issuer, audience, and expiration.
- Be validated without querying the database during normal protected API requests.
- Not be persisted by the server as active session records.

The concrete signing algorithm, key source, issuer, audience, and lifetime values will be configurable.

### Refresh Tokens

Refresh tokens will be opaque, cryptographically secure random values.

They will:

- Have a longer, configurable lifetime than access tokens.
- Be associated with a user session.
- Be stored server-side only as a one-way hash or verifier.
- Never be persisted or logged in plaintext.
- Be treated as single-use credentials.
- Be rotated whenever a session is refreshed.
- Be revocable individually or as part of all sessions belonging to a user.

### Refresh Token Rotation

When a valid refresh token is used:

1. The existing refresh token will be consumed.
2. A new access token will be issued.
3. A new refresh token will be issued.
4. The previous refresh token will be invalidated atomically.

If an invalidated refresh token is reused, the entire related token family will be revoked.

This behavior is intended to limit the impact of refresh-token theft and replay.

### Logout

Logging out will revoke the current refresh-token session.

An access token already issued before logout may remain valid until its expiration because access-token validation does not require a database lookup.

A separate operation may revoke all refresh-token sessions belonging to a user.

### User and Role State Changes

Disabling a user will prevent:

- New authentication.
- Session refresh.
- Creation of new sessions.

Role changes and user disablement will apply immediately to future access tokens.

Previously issued access tokens may continue to contain earlier claims until they expire.

### Client Storage

Clients must treat access and refresh tokens as sensitive credentials.

Mobile applications should store tokens using the platform's secure storage capabilities.

The server will not require clients to retain the user's password after successful authentication.

## Consequences

### Positive

- Protected API requests can be authorized without a database lookup.
- Refresh-token rotation limits replay risk.
- Sessions can be revoked without storing access tokens.
- The strategy works well for mobile and web clients.
- Server-side refresh-token state supports logout and administrative revocation.

### Negative

- Logout cannot immediately invalidate an already-issued access token without introducing additional server-side validation.
- Role and account-state changes may not affect an existing access token until it expires.
- Refresh-token rotation requires transactional persistence.
- Token-family tracking introduces additional session-management complexity.

## Alternatives Considered

### Long-lived JWT Access Tokens Without Refresh Tokens

Rejected because stolen access tokens would remain valid for an extended period and could not be revoked easily.

### Persisting Plaintext Refresh Tokens

Rejected because a database or log disclosure would expose directly usable credentials.

### Database Validation for Every Access Token

Rejected because it removes the main benefit of short-lived self-contained access tokens and increases infrastructure dependency for every protected request.

### Immediate Access Token Revocation

Deferred because it would require a denylist, token version lookup, or another server-side state check during access-token validation.

## Deferred Decisions

The following details will be defined in the implementation plan or configuration:

- Access-token lifetime.
- Refresh-token lifetime.
- JWT signing algorithm.
- Signing-key source and rotation.
- Issuer and audience values.
- Required JWT claims.
- Clock-skew tolerance.
- Refresh-token persistence schema.
- Session and device metadata.
- Maximum number of active sessions per user.