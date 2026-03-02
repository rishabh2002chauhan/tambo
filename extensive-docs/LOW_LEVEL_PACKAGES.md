# Low Level Overview: Packages

Documentation of the code files within the `packages/` directory.

## `packages/backend` (Tambo Engine)

The core logic for AI orchestration and streaming.

### Core Files

- **`src/tambo-backend.ts`**: The main entry point for the backend engine. Orchestrates LLM calls, tools, and streaming.
- **`src/systemTools.ts`**: Defines built-in tools available to the AI.

### Services (`src/services/`)

- **`llm/`**: Adapters for various LLM providers.
  - `llm-service.ts`: Abstract interface for LLMs.
  - `openai-service.ts`, `anthropic-service.ts`, etc.
- **`decision-loop/`**: The core AI "think" loop.
  - `agent-loop.ts`: Manages the iterative process of thinking, calling tools, and responding.
- **`tool/`**: Logic for tool discovery and execution.
  - `tool-service.ts`: Manages both server-side and client-side tools.
- **`suggestion/`**: Generates predictive prompt suggestions for users.
- **`agui/`**: Utilities for the AG-UI protocol.

### Utilities (`src/util/`)

- **`component-streaming.ts`**: Logic for streaming partial JSON props to React components.
- **`response-parsing.ts`**: Parses raw LLM output into structured events.
- **`thread-to-model-message-conversion.ts`**: Converts database messages into LLM-compatible formats.

---

## `packages/core` (Shared logic)

Foundational types and utilities shared across the monorepo.

### Configuration & Models

- **`src/llms/`**: Configuration for LLM models and providers.
  - `llm.config.ts`, `llm-config-types.ts`.
  - `models/`: Provider-specific model definitions (OpenAI, Anthropic, etc.).
- **`src/ai-providers.ts`**: Enum of supported AI providers.

### Utilities

- **`src/json.ts`**, **`src/typeutils.ts`**: General-purpose TypeScript utilities.
- **`src/encrypt.ts`**: Encryption/decryption helpers for sensitive data.
- **`src/auth/`**: Shared authentication logic (e.g., email domain validation).
- **`src/mcp-utils.ts`**: Utilities for working with the Model Context Protocol.
- **`src/strictness/`**: Logic for ensuring LLM outputs adhere to strict JSON schemas.

---

## `packages/db` (Database Layer)

Persistence logic using Drizzle ORM.

### Schema & Types

- **`src/schema.ts`**: The main database schema definition (Projects, Threads, Messages, Users).
- **`src/types.ts`**: TypeScript types derived from the database schema.

### Operations (`src/operations/`)

- **`project.ts`**, **`thread.ts`**, **`messages.ts`**, **`runs.ts`**: CRUD operations for specific entities.
- **`tambo-user.ts`**: Operations for managing Tambo Cloud users.

---

## `packages/ui-registry` (Component Registry)

Manages the catalog of generative UI components.

### Components (`src/components/`)

A collection of pre-built generative components:

- `graph/`, `map/`, `form/`, `message-input/`, `message-thread-panel/`, etc.
- Each component directory contains:
  - `config.json`: Metadata for the AI (description, props schema).
  - `[name].tsx`: The React implementation.

### Styles (`src/styles/`)

- `globals-v3.css`, `globals-v4.css`: Base styles for registry components.
- `tailwind.config.ts`: Tailwind configuration for the registry.

---

## `packages/react-ui-base`

Fundamental UI components used in the dashboard.

- **`src/components/`**: Standard UI primitives (Button, Input, etc.).
