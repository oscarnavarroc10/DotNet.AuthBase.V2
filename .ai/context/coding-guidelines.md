# Coding Guidelines

This file defines the coding standards for DotNet.AuthBase.V2 C# code. All AI agents acting as the Backend Engineer persona must follow these guidelines.

> **Status:** Placeholder — Guidelines will be finalized before implementation begins. The conventions below are initial defaults based on .NET community standards.

---

## Language and Framework

- Use **C# 12** and **.NET 8** features where appropriate.
- Use **ASP.NET Core 8** for HTTP concerns.
- Use **Entity Framework Core 8** for data access.
- Target the latest stable LTS version of .NET.

## Naming Conventions

| Element | Convention | Example |
|---------|-----------|---------|
| Classes | PascalCase | `TokenService` |
| Interfaces | `I` + PascalCase | `ITokenService` |
| Methods | PascalCase | `GenerateAccessToken` |
| Properties | PascalCase | `ExpiresAt` |
| Private fields | `_` + camelCase | `_tokenRepository` |
| Local variables | camelCase | `accessToken` |
| Constants | PascalCase | `DefaultTokenLifetime` |
| Namespaces | PascalCase, dot-separated | `DotNet.AuthBase.Core.Services` |

## Code Style

- Prefer `var` when the type is obvious from the right-hand side.
- Use expression-bodied members only when they improve readability.
- Avoid deeply nested code. Extract methods to reduce nesting.
- Use `async`/`await` for all I/O-bound operations. Never use `.Result` or `.Wait()`.
- Prefer `IReadOnlyList<T>` over `List<T>` for return types unless mutation is intended.

## XML Documentation

All public types and members must have XML documentation comments:

```csharp
/// <summary>
/// Generates a signed JWT access token for the specified user.
/// </summary>
/// <param name="userId">The unique identifier of the user.</param>
/// <returns>A signed JWT string.</returns>
public string GenerateAccessToken(Guid userId) { ... }
```

## Error Handling

- Use custom exception types for domain errors (e.g., `InvalidCredentialsException`).
- Never expose internal exception details in API responses.
- Log errors at the appropriate level using `ILogger<T>`.
- Do not swallow exceptions silently.

## Dependency Injection

- Register all services through the ASP.NET Core DI container.
- Prefer constructor injection.
- Avoid service locator patterns.

## Configuration

- Never hardcode configuration values. Use `IOptions<T>` or `IConfiguration`.
- Do not commit `appsettings.Development.json` or any file containing real credentials.

## Testing

- Use **xUnit** for all tests.
- Use **Moq** for mocking.
- Name tests using the pattern: `MethodName_Scenario_ExpectedOutcome`.
- Each test method should test one behavior.
