# SPEC-0001: Authentication Foundation

- **Status:** In Review
- **Related ADR:** ADR-0001 Base Architecture

---

# Overview

This specification defines the minimum authentication capabilities provided by DotNet.AuthBase.V2.

The goal is to provide a secure, reusable authentication foundation for ASP.NET Core applications using JWT-based authentication.

This specification focuses on authentication, session management, and basic role-based authorization.

---

# Goals

The system shall provide:

- User registration
- User authentication
- JWT access tokens
- Refresh tokens
- Refresh token rotation
- Session refresh
- Logout
- Current authenticated user
- User roles
- Role-based authorization
- Secure credential management
- User enable/disable

---

# Functional Requirements

## Registration

- Public registration shall be disabled by default.
- When public registration is enabled, the system shall allow users to register using an email and password.
- When public registration is disabled, users may only be created through an authorized administrative operation.
- Public registration shall assign only a server-controlled default role.
- Clients shall not be allowed to select or assign roles during registration.

---

## Authentication

The system shall:

- Authenticate users using email and password.
- Return an Access Token.
- Return a Refresh Token.
- Reject invalid credentials.
- Reject disabled users.

---

## Credential Security

The system shall:

- Never store or log passwords in plaintext.
- Protect passwords using an adaptive salted password-hashing mechanism.
- Never expose passwords, password hashes, or credential material in responses.

---

## Session Management

The system shall:

- Refresh an authenticated session using a valid refresh token.
- Issue refresh tokens with a finite expiration.
- Treat refresh tokens as single-use credentials.
- Rotate the refresh token whenever a session is refreshed.
- Invalidate the previous refresh token when rotation succeeds.
- Reject expired, revoked, reused, or otherwise invalid refresh tokens.
- Revoke the current refresh-token session on logout.
- Allow authorized administrators to revoke all active sessions for a user.
- Reject session refresh attempts from disabled users.

---

## User Information

The system shall expose the current authenticated user's:

- User identifier.
- Email.
- Assigned roles.
- Enabled or disabled status.

The system shall not expose passwords, password hashes, tokens, token metadata, or other credential material.

---

## Authorization

The system shall support:

- Role-based authorization.
- Multiple roles per user.
- Server-controlled role assignment.
- Role changes performed only through authorized administrative operations.
- Access being granted when the authenticated user has a required role.
- Access being denied when the authenticated user does not have a required role.

---

# Non-functional Requirements

The authentication system shall be:

- Secure by default.
- Access token validation shall not require a database lookup.
- Testable.
- Extensible.
- Framework-independent where possible.

---

# Out of Scope

The following features are intentionally excluded from this specification:

- MFA
- External Login Providers
- Email Verification
- Forgot Password
- Password Reset
- Permissions
- Passkeys
- SAML
- OpenID Connect Provider
- Multi-tenancy

---

# Acceptance Criteria

## Registration Enabled

Given public registration is enabled

When a new user registers with valid information

Then the account is created with the default server-assigned role.

---

## Registration Disabled

Given public registration is disabled

When an anonymous user attempts to register

Then the request is rejected.

---

## Login

Given valid credentials

When the user authenticates

Then the system returns a valid Access Token and Refresh Token.

---

## Invalid Login

Given invalid credentials

When the user authenticates

Then authentication is rejected.

---

## Disabled User

Given a disabled user

When authentication is attempted

Then authentication is rejected.

---

## Refresh

Given a valid Refresh Token

When the client requests a session refresh

Then the system returns a new Access Token and a new Refresh Token.

---

## Logout

Given an authenticated session

When the user logs out

Then the current refresh-token session is revoked.

---

## Current User

Given an authenticated user

When requesting the current user

Then the response contains only the allowed user information and no credential material.

---

## Authorization - Allowed

Given an authenticated user with the required role

When accessing a protected endpoint

Then access is granted.

---

## Authorization - Denied

Given an authenticated user without the required role

When accessing a protected endpoint

Then access is denied.