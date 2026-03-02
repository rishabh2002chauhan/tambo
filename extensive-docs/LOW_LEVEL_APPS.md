# Low Level Overview: Apps

Documentation of the code files within the `apps/` directory.

## `apps/api` (Tambo Cloud Backend)

The core NestJS service for the Tambo Cloud platform.

### Core Files
- **`src/main.ts`**: Entry point. Sets up NestJS, Sentry, OpenTelemetry, and Swagger.
- **`src/app.module.ts`**: The root module that imports all other feature modules.
- **`src/app.controller.ts`**: Root controller for basic health checks.
- **`src/app.service.ts`**: Root service for application-wide logic.
- **`src/config.service.ts`**: Centralized configuration management, reading from environment variables.
- **`src/generate-config.ts`**: Utility to generate a snapshot of the current configuration.
- **`src/telemetry.ts`**: OpenTelemetry instrumentation setup.
- **`src/sentry.ts`**: Sentry error tracking initialization.

### Modules & Features
- **`src/v1/`**: Implements the V1 API version.
  - `v1.module.ts`, `v1.controller.ts`, `v1.service.ts`: Core V1 API logic.
  - `v1-tool-results.ts`: Logic for handling tool execution results.
  - `v1-tool-conversions.ts`: Converts tool-related data between formats.
  - `v1-client-tools.ts`: Management of client-side tools.
  - `v1-conversions.ts`: Utilities for converting between internal and API models.
  - `v1.errors.ts`: V1-specific error definitions.
  - `v1-pagination.ts`: Pagination logic for V1 lists.
  - `dto/`: Data Transfer Objects for V1 (e.g., `event.dto.ts`, `message.dto.ts`, `run.dto.ts`).
  - `guards/`: Security guards like `v1-thread-in-project-guard.ts`.
  - `utils/`: Utilities like `get-v1-context-info.ts`.
- **`src/threads/`**: Manages chat threads and messages.
  - `threads.module.ts`, `threads.controller.ts`, `threads.service.ts`.
  - `dto/`: DTOs for thread operations (e.g., `advance-thread.dto.ts`, `generate-component.dto.ts`).
  - `util/`: Extensive utilities for message handling, tool tracking, and streaming (e.g., `streaming.ts`, `tool-call-tracking.ts`).
  - `guards/`: Security guards for thread access (e.g., `thread-in-project-guard.ts`).
- **`src/projects/`**: Project management and API key handling.
  - `projects.module.ts`, `projects.controller.ts`, `projects.service.ts`.
  - `entities/`: Database entity definitions for projects (e.g., `project.entity.ts`, `api-key.entity.ts`).
  - `dto/`: DTOs for project management.
  - `guards/`: API key and project access guards.
- **`src/registry/`**: Component registry synchronization.
  - `registry.module.ts`, `registry.controller.ts`, `registry.service.ts`.
- **`src/mcp-server/`**: Model Context Protocol implementation.
  - `server.ts`: The MCP server instance.
  - `prompts.ts`, `resources.ts`, `elicitations.ts`: MCP feature implementations.
- **`src/oauth/`**: OAuth 2.0 flow handling for third-party integrations.
- **`src/users/`**: User profile and management logic.
  - `entities/`: Auth and User entities.
- **`src/audio/`**: Voice and audio processing (transcription).
- **`src/storage/`**: File storage abstraction (S3/Local).
- **`src/scheduler/`**: Background jobs and cron tasks.
- **`src/common/`**: Shared components across the API.
  - `services/`: Global services like `analytics.service.ts`, `email.service.ts`, `storage-config.service.ts`.
  - `filters/`: Exception filters for domain and HTTP errors.
  - `middleware/`: Request logging and SDK version checking.
  - `utils/`: Context extraction and OAuth utilities.
  - `emails/`: React-based email templates (e.g., `welcome.tsx`, `message-limit.tsx`).
  - `decorators/`, `dto/`: Shared decorators and DTOs.

---

## `apps/web` (Tambo Cloud Dashboard)

The Next.js 15 frontend for managing Tambo projects.

### App Router (`app/`)
- **`layout.tsx`**, **`providers.tsx`**: Root layout and global context providers.
- **`(authed)/`**: Protected routes for the dashboard.
- **`login/`**, **`unauthorized/`**: Auth pages.
- **`api/`**: API routes for webhooks and auth.
- **`trpc/`**: tRPC client configuration.
- **`blog/`**: Marketing blog pages.
- **`demo/`**, **`slack/`**, **`subscribe/`**: Specialized feature pages.

### Components (`components/`)
- **`ui/`**: Reusable primitive components.
- **`sections/`**: Page sections like `hero.tsx`, `pricing.tsx`.
- **`dashboard-components/`**: UI for project management and onboarding.
- **`observability/`**: UI for viewing logs and traces.
- **`smoketest/`**: Internal verification components.
- **`auth/`**: Auth forms.

### Server Logic (`server/`)
- **`api/root.ts`**: Main tRPC router.
- **`api/routers/`**: Specific routers for projects, threads, etc.
- **`api/trpc.ts`**: tRPC server initialization.

---

## `apps/docs-mcp`

Specialized documentation app for MCP.
- **`app/page.tsx`**, **`app/layout.tsx`**.
- **`lib/`**: MCP-related utilities.

---

## `apps/test-mcp-server`

Reference MCP server.
- **`src/index.ts`**, **`src/server.ts`**.
