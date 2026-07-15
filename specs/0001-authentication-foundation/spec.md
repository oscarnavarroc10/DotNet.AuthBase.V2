# SPEC-0001: Authentication Foundation

- **Status:** Proposed
- **Related ADR:** ADR-0001 Base Architecture

---

# Overview

This specification defines the minimum authentication capabilities provided by DotNet.AuthBase.V2.

The goal is to provide a secure, reusable authentication foundation for ASP.NET Core applications using JWT-based authentication.

This specification focuses on authentication and session management only.

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
- Password hashing
- User enable/disable

---

# Functional Requirements

## Registration

- The system shall support public registration when enabled.
- The system shall allow administrator-only registration when public registration is disabled.

---

## Authentication

The system shall:

- Authenticate users using email and password.
- Return an Access Token.
- Return a Refresh Token.
- Reject invalid credentials.
- Reject disabled users.

---

## Session Management

The system shall:

- Refresh expired access tokens using a valid refresh token.
- Rotate refresh tokens.
- Revoke refresh tokens.
- Allow logout.

---

## User Information

The system shall expose:

- Current authenticated user.
- Assigned roles.

---

## Authorization

The system shall support:

- Role-based authorization.
- Multiple roles per user.

---

# Non-functional Requirements

The authentication system shall be:

- Secure by default.
- Stateless.
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

## Login

Given valid credentials

When the user authenticates

Then the system returns a valid Access Token and Refresh Token.

---

## Refresh

Given a valid Refresh Token

When the Access Token expires

Then the system issues a new Access Token.

---

## Authorization

Given an authenticated user

When accessing a protected endpoint

Then authorization is evaluated using assigned roles.