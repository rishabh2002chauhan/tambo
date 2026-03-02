# High Level Overview

Tambo AI is a generative UI toolkit for React. This repository is a monorepo containing the SDK, backend services, CLI, and supporting packages.

## Repository Structure

### `apps/`

Contains the primary applications of the Tambo ecosystem.

- **`apps/api/`**: The NestJS-based backend for Tambo Cloud. It handles project management, user authentication, thread storage, and orchestrates the AI decision loop.
- **`apps/web/`**: The Next.js dashboard for Tambo Cloud, where users can manage projects, API keys, and view analytics.
- **`apps/docs-mcp/`**: Specialized documentation or tools related to the Model Context Protocol (MCP).
- **`apps/test-mcp-server/`**: A reference implementation of an MCP server used for testing integrations.

### `packages/`

Shared libraries and utilities used across the applications and SDK.

- **`packages/backend/`**: Core logic for AI orchestration, streaming components, and LLM provider integrations. This is the engine that powers the AI responses.
- **`packages/core/`**: Shared TypeScript types, schemas, and foundational logic used by both frontend and backend.
- **`packages/db/`**: Drizzle ORM schemas and migrations for the Tambo Cloud database.
- **`packages/ui-registry/`**: Logic for managing and syncing component registries, allowing the AI to know which UI components are available.
- **`packages/react-ui-base/`**: Fundamental UI components and styles used within the Tambo dashboard and SDK.
- **`packages/testing/`**: Shared testing utilities and mocks.

### `react-sdk/`

The core product for developers. It provides React hooks (`useTambo`, `useTamboThreadInput`) and providers (`TamboProvider`) to integrate generative UI into any React application.

### `cli/`

The Tambo Command Line Interface. It assists developers in creating new projects, syncing component registries, and managing their Tambo environment.

### `create-tambo-app/`

An `npx` utility for quickly scaffolding new Tambo-powered React applications, similar to `create-next-app`.

### `scripts/`

A collection of bash and TypeScript scripts for repository maintenance, database initialization, and cloud deployment.

### `docs/`

The source code for the official Tambo documentation (docs.tambo.co).

### `showcase/`

Example applications and templates demonstrating the capabilities of Tambo AI.

### `plugins/`

Extensions and plugins for the Tambo ecosystem.

## Low Level Documentation Index

- **`extensive-docs/LOW_LEVEL_APPS.md`**: Document every code file in the `apps/` directory.
- **`extensive-docs/LOW_LEVEL_PACKAGES.md`**: Document every code file in the `packages/` directory.
- **`extensive-docs/LOW_LEVEL_SDK_CLI.md`**: Document every code file in the `react-sdk/`, `cli/`, and `create-tambo-app/` directories.
- **`extensive-docs/LOW_LEVEL_DOCS_SHOWCASE.md`**: Document every code file in the `docs/`, `showcase/`, and `plugins/` directories.
- **`extensive-docs/LOW_LEVEL_OTHER.md`**: Document root-level configuration files and scripts in `scripts/`.

## Feature Mapping

| Feature               | Primary Folder(s)                        |
| --------------------- | ---------------------------------------- |
| AI Orchestration      | `packages/backend`, `apps/api`           |
| Component Streaming   | `react-sdk`, `packages/backend`          |
| MCP Integration       | `packages/core`, `react-sdk`, `apps/api` |
| Dashboard / UI        | `apps/web`, `packages/react-ui-base`     |
| Local Tool Execution  | `react-sdk`                              |
| CLI / Developer Tools | `cli`, `create-tambo-app`                |
| Data Persistence      | `apps/api`, `packages/db`                |
