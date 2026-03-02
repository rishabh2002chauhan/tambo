# Low Level Overview: SDK & CLI

Documentation of the code files within the `react-sdk/`, `cli/`, and `create-tambo-app/` directories.

## `react-sdk` (Tambo React SDK)

The core React package for integrating Tambo AI into applications.

### Public API (`src/index.ts`)
The primary entry point, exporting providers, hooks, and types for version 1.

### Providers (`src/v1/providers/`)
- **`tambo-v1-provider.tsx`**: The main context provider for Tambo apps.
- **`tambo-v1-stream-context.tsx`**: Manages real-time AI event streams.
- **`tambo-v1-thread-input-provider.tsx`**: Context for the user's chat input.
- **`tambo-v1-stub-provider.tsx`**: A mock provider for testing.

### Hooks (`src/v1/hooks/`)
- **`use-tambo-v1.ts`**: The root hook for accessing the AI state.
- **`use-tambo-v1-thread-input.ts`**: Provides functions for submitting messages.
- **`use-tambo-v1-messages.ts`**: Manages the message history.
- **`use-tambo-v1-stream-status.ts`**: Tracks the status of the current AI run (thinking, streaming, idle).
- **`use-tambo-v1-component-state.ts`**: Hook for accessing the state of interactable components.
- **`use-tambo-v1-suggestions.ts`**: Logic for predictive prompt suggestions.

### Utilities (`src/v1/utils/`)
- **`stream-handler.ts`**: Logic for parsing SSE event streams.
- **`tool-executor.ts`**: Executes local client-side tools.
- **`component-renderer.tsx`**: Logic for matching AI names to React components.
- **`event-accumulator.ts`**: Buffers and merges incoming streaming props.
- **`json-patch.ts`**: Applies partial JSON updates to component props.

---

## `cli` (Tambo Command Line Tool)

The CLI for managing Tambo projects and component registries.

### Core Entry Point (`src/cli.ts`)
Sets up the CLI command structure using a library like Commander or Yargs.

### Commands (`src/commands/`)
- **`init.ts`**: Initializes a new Tambo project in the current folder.
- **`auth.ts`**: Handles developer login and authentication with Tambo Cloud.
- **`add/`**: Sub-commands for adding components or features (e.g., Tailwind).
- **`list/`**: Lists available components in the registry.
- **`update.ts`**, **`upgrade/`**: Manages project and package updates.
- **`migrate.ts`**: Assists with version migrations.

### Logic & Utilities (`src/lib/` & `src/utils/`)
- **`api-client.ts`**: The client for communicating with the Tambo Cloud API.
- **`device-auth.ts`**: Logic for browser-based CLI authentication.
- **`framework-detection.ts`**: Automatically detects if a project is using Next.js, Vite, or other frameworks.
- **`package-manager.ts`**: Logic for installing dependencies using npm, yarn, or pnpm.
- **`telemetry.ts`**: Optional anonymous usage tracking for the CLI.

---

## `create-tambo-app` (Scaffolding Tool)

The tool used via `npx create-tambo-app`.

### Core Logic (`src/index.ts`)
Prompts the user for project details and copies templates from the `templates/` directory to the target project.
- Handles Git initialization and initial package installation.
