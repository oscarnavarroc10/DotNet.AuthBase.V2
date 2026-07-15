# AI Agent Configuration

This directory contains configuration, personas, prompt templates, and context files used by AI agents working on DotNet.AuthBase.V2.

## Purpose

AI agents in this project operate under a structured, Spec-Driven Development workflow. This directory provides the rules, roles, and reusable templates that ensure consistent, safe, and traceable AI assistance.

## Directory Structure

```
.ai/
├── README.md          # This file
├── personas/          # Role definitions for AI agents
├── prompts/           # Reusable prompt templates for common tasks
└── context/           # Project rules and guidelines injected into AI sessions
```

## How to Use

### Personas

Before starting an AI-assisted task, select the appropriate persona from `.ai/personas/`. Each persona defines the role, responsibilities, and constraints for a specific type of task.

### Prompts

Use the prompt templates in `.ai/prompts/` as starting points for common tasks such as reviewing specifications, implementing features, or creating tests. Fill in the placeholders marked with `[brackets]` before submitting.

### Context Files

The files in `.ai/context/` contain project-wide rules and guidelines. Inject them into your AI session context to ensure the agent understands the project conventions.

## Rules

All AI agents must comply with the rules defined in [`docs/AI_RULES.md`](../docs/AI_RULES.md).
