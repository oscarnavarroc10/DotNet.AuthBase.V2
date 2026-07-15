# DotNet.AuthBase.V2

Production-ready ASP.NET Core authentication foundation built with Spec-Driven Development, AI-assisted engineering, JWT, refresh tokens, and automated testing.

> **Note:** This initial pull request contains documentation and repository structure only. No application code, authentication logic, or infrastructure has been implemented yet.

---

## Overview

DotNet.AuthBase.V2 is a reusable authentication foundation for ASP.NET Core applications. It is designed to be modular, secure, and thoroughly tested. The project follows a **Spec-Driven Development (SDD)** workflow, meaning all features must be specified and approved before any production code is written.

## Repository Structure

```
DotNet.AuthBase.V2/
├── README.md               # This file
├── docs/                   # Project documentation
│   ├── VISION.md           # Project vision and goals
│   ├── ARCHITECTURE.md     # Architecture decisions and diagrams
│   ├── TECH_STACK.md       # Technology choices and rationale
│   ├── AI_RULES.md         # Rules governing AI agent behavior
│   └── adr/          # Architecture Decision Records (ADRs)
├── specs/                  # Feature specifications (source of truth)
├── src/                    # Application source code (not yet implemented)
├── tests/                  # Automated tests (not yet implemented)
└── .ai/                    # AI agent configuration
    ├── personas/            # Role definitions for AI agents
    ├── prompts/             # Reusable prompt templates
    └── context/             # Project rules and guidelines for AI agents
```

## Spec-Driven Development

This project follows SDD principles:

1. **Specifications first** — Every feature begins with a written specification in `specs/`.
2. **Review before code** — Specifications must be approved before implementation starts.
3. **Decisions documented** — Architecture decisions are recorded in `docs/adr/`.
4. **AI-assisted, human-approved** — AI agents assist with drafting, but humans approve all specs and architectural decisions.

## Getting Started

This repository is in its initial documentation phase. Implementation will begin once the foundational specifications and architecture decisions are approved.

See [`docs/VISION.md`](docs/VISION.md) for the project vision and [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) for the planned architecture.

## Contributing

Please read [`docs/AI_RULES.md`](docs/AI_RULES.md) before using AI agents in this project. All contributions must trace back to an approved specification.

## License

This project is licensed under the MIT License.
