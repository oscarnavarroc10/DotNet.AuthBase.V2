# ADR-0003: Password Hashing Strategy

- **Status:** Proposed
- **Date:** 2026-07-15
- **Related Specification:** SPEC-0001 Authentication Foundation

## Context

DotNet.AuthBase.V2 must securely protect user passwords while avoiding custom cryptographic implementations.

Passwords must never be stored, logged, or returned in plaintext.

The selected strategy must:

- Use adaptive and salted password hashing.
- Support verification without recovering the original password.
- Allow hashing parameters to evolve over time.
- Detect when an existing password hash should be upgraded.
- Keep cryptographic implementation details outside the Domain and Application layers.

## Decision

Password hashing will be implemented in the Infrastructure layer using the password-hashing capabilities provided by ASP.NET Core Identity.

Application code will depend on an explicit password-hashing contract rather than directly depending on ASP.NET Core Identity.

The implementation will:

- Generate a unique salt as part of every password hash.
- Use an adaptive password-based key derivation mechanism.
- Store only the resulting encoded password hash.
- Verify passwords using the framework-provided verification mechanism.
- Detect hashes that require rehashing.
- Generate a new hash after successful authentication when an existing hash uses outdated parameters.
- Avoid exposing hashing parameters or framework-specific types outside Infrastructure.
- Never log plaintext passwords, password hashes, or password-verification inputs.

Password hashing parameters may be configured in Infrastructure, but they must not be weakened below the secure defaults selected by the framework without a separate architectural decision.

## Password Handling

Plaintext passwords may exist in application memory only for the minimum time required to:

- Register a user.
- Authenticate a user.
- Change a password.
- Reset a password in a future specification.

Plaintext passwords will not be:

- Persisted.
- Cached.
- Included in logs.
- Included in telemetry.
- Included in exceptions.
- Returned in API responses.

## Hash Upgrade

When password verification indicates that an existing hash uses outdated parameters:

1. Authentication may continue if the password is valid.
2. A new password hash will be generated using the current configuration.
3. The stored hash will be replaced with the upgraded hash.

The upgrade must not require the user to reset a valid password.

## Layering

The password-hashing contract will belong to the Application layer.

The ASP.NET Core Identity implementation will belong to the Infrastructure layer.

The Domain layer will not reference:

- ASP.NET Core Identity.
- Cryptographic libraries.
- Password-hashing algorithms.
- Framework-specific password-hashing types.

## Consequences

### Positive

- Avoids implementing password cryptography manually.
- Uses a framework-supported and version-aware hashing mechanism.
- Supports automatic hash upgrades.
- Keeps the Domain and Application layers independent from the hashing framework.
- Allows the implementation to be replaced behind an application contract.

### Negative

- Infrastructure becomes dependent on ASP.NET Core Identity password-hashing components.
- Stored hashes are coupled to the selected framework format.
- Migrating to a different hashing implementation may require supporting multiple hash formats during a transition period.

## Alternatives Considered

### Custom PBKDF2 Implementation

Rejected because implementing and maintaining cryptographic behavior directly would introduce unnecessary security risk.

### BCrypt Library

Considered a valid alternative but rejected for the initial version because ASP.NET Core Identity already provides password hashing, verification, versioning, configuration, and rehash detection within the selected platform.

### Reversible Password Encryption

Rejected because authentication does not require recovering the original password and reversible storage would increase the impact of a credential-store compromise.

### Unsalted General-Purpose Hashing

Rejected because algorithms intended for general data hashing are unsuitable for password storage and do not provide the required adaptive cost.

## Deferred Decisions

The following details will be defined during implementation planning or configuration:

- Exact hashing parameters.
- Configuration binding.
- Hash-upgrade persistence flow.
- Behavior when persistence of an upgraded hash fails.
- Migration strategy if a different password-hashing provider is adopted.