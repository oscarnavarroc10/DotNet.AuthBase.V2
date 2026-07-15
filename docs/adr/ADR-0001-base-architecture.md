# ADR-0001: Base Architecture

* **Status:** Proposed
* **Date:** 2026-07-14

## Context

DotNet.AuthBase.V2 será una base reutilizable para implementar autenticación y autorización en aplicaciones ASP.NET Core.

El proyecto necesita una arquitectura que separe responsabilidades, facilite las pruebas y permita evolucionar sin introducir complejidad innecesaria desde el inicio.

## Decision

La solución se organizará inicialmente en cuatro proyectos:

* `DotNet.AuthBase.V2.Api`
* `DotNet.AuthBase.V2.Application`
* `DotNet.AuthBase.V2.Domain`
* `DotNet.AuthBase.V2.Infrastructure`

Las dependencias deberán seguir estas reglas:

* `Domain` no dependerá de otros proyectos de la solución.
* `Application` podrá depender de `Domain`.
* `Infrastructure` podrá depender de `Application` y `Domain`.
* `Api` actuará como *Composition Root* y podrá depender de `Application` e `Infrastructure`.

Este ADR no define tecnologías concretas de persistencia, autenticación, validación, mensajería o manejo de casos de uso.

## Consequences

### Positive

* Separación clara de responsabilidades.
* Mayor facilidad para realizar pruebas.
* Menor acoplamiento con frameworks e infraestructura.
* Posibilidad de evolucionar la arquitectura mediante futuros ADRs.

### Negative

* La solución tendrá más proyectos que una aplicación de un solo proyecto.
* Será necesario mantener disciplina sobre la dirección de dependencias.

## Deferred Decisions

Los siguientes temas se definirán mediante futuros ADRs o Specifications:

* Controllers o Minimal APIs.
* Persistencia y motor de base de datos.
* Entity Framework Core.
* JWT y Refresh Tokens.
* Hashing de contraseñas.
* Roles y permisos.
* CQRS o MediatR.
* Manejo de errores.
* Estrategia de pruebas.
