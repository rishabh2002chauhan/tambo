# Low Level Overview: Apps

Documentation of the code files within the `apps/` directory.

## `apps/api` (Tambo Cloud Backend)

The core NestJS service for the Tambo Cloud platform.

### Core Files
- **`src/main.ts`**: Entry point. Sets up NestJS, Sentry, OpenTelemetry, and Swagger.
- **`src/app.module.ts`**: The root module that imports all other feature modules.
- **`src/config.service.ts`**: Centralized configuration management, reading from environment variables.
- **`src/telemetry.ts`**: OpenTelemetry instrumentation setup.
- **`src/sentry.ts`**: Sentry error tracking initialization.

### Modules & Features
- **`src/v1/`**: Implements the V1 API version.
  - `v1.module.ts`, `v1.controller.ts`, `v1.service.ts`: Core V1 API logic.
  - `v1-tool-results.ts`: Logic for handling tool execution results.
  - `v1-client-tools.ts`: Management of client-side tools.
  - `v1-conversions.ts`: Utilities for converting between internal and API models.
- **`src/threads/`**: Manages chat threads and messages.
  - `threads.module.ts`, `threads.controller.ts`, `threads.service.ts`.
  - `guards/`: Security guards for thread access.
- **`src/projects/`**: Project management and API key handling.
  - `projects.module.ts`, `projects.controller.ts`, `projects.service.ts`.
  - `entities/`: Database entity definitions for projects.
- **`src/registry/`**: Component registry synchronization.
  - `registry.module.ts`, `registry.controller.ts`, `registry.service.ts`.
- **`src/mcp-server/`**: Model Context Protocol implementation.
  - `server.ts`: The MCP server instance.
  - `prompts.ts`, `resources.ts`, `elicitations.ts`: MCP feature implementations.
- **`src/oauth/`**: OAuth 2.0 flow handling for third-party integrations.
- **`src/users/`**: User profile and management logic.
- **`src/audio/`**: Voice and audio processing (transcription).
- **`src/storage/`**: File storage abstraction (S3/Local).
- **`src/scheduler/`**: Background jobs and cron tasks.
- **`src/common/`**: Shared filters, middleware, decorators, and services (database, analytics, logger).

---

## `apps/web` (Tambo Cloud Dashboard)

The Next.js 15 frontend for managing Tambo projects.

### App Router (`app/`)
- **`layout.tsx`**, **`providers.tsx`**: Root layout and global context providers (Auth, Theme, tRPC).
- **`(authed)/`**: Protected routes for the dashboard, including project management and CLI sessions.
- **`login/`**, **`unauthorized/`**: Auth-related pages.
- **`api/`**: Next.js API routes for webhooks and internal integrations.
- **`trpc/`**: tRPC client configuration and endpoint.
- **`blog/`**: Marketing blog pages using MDX.

### Components (`components/`)
- **`ui/`**: Reusable primitive components (Button, Input, Card, etc.) based on Shadcn UI.
- **`sections/`**: High-level page sections (Hero, Pricing, Footer).
- **`dashboard-components/`**: Feature-specific UI for the dashboard (ProjectTable, OnboardingWizard).
- **`observability/`**: UI for viewing AI logs, traces, and thread history.
- **`auth/`**: Authentication forms and wrappers.
- **`smoketest/`**: Internal tools for verifying system functionality.

### Server Logic (`server/`)
- **`api/root.ts`**: The main tRPC router definition.
- **`api/trpc.ts`**: tRPC server initialization and middleware.

---

## `apps/docs-mcp`

A specialized Next.js app for MCP documentation.
- **`app/page.tsx`**: Main landing page.
- **`lib/`**: Utilities for fetching MCP-related data.

---

## `apps/test-mcp-server`

A reference MCP server for testing.
- **`src/index.ts`**: Defines test tools and resources.
- **`src/server.ts`**: Initializes the MCP server transport.
