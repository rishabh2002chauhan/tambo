# Low Level Overview: Scripts & Root

Documentation of code files within the `scripts/` directory and at the repository root.

## `scripts/` (Maintenance & Tools)

A collection of utility scripts for managing the repository.

### Cloud Maintenance (`scripts/cloud/`)
- **`init-database.sh`**: Initializes the Tambo Cloud database (Postgres) and runs Drizzle migrations.
- **`tambo-setup.sh`**: Bootstraps the local Tambo Cloud development environment.
- **`tambo-build.sh`**: Builds all apps and packages for production.
- **`tambo-start.sh`**: Starts the Tambo Cloud backend and dashboard.
- **`tambo-stop.sh`**: Stops all local Tambo processes.
- **`tambo-logs.sh`**: Aggregates logs from all running services.
- **`tambo-psql.sh`**: Direct access to the Postgres database.
- **`smoke-mcp.sh`**: Runs a series of smoke tests to verify MCP functionality.

### Core Scripts
- **`dev-local.sh`**: A helper script to run the API and Web frontend simultaneously.
- **`debug-stream.ts`**: A utility script for debugging SSE event streams.
- **`workspace-packages.mjs`**: Utilities for working with the monorepo workspace structure.
- **`find-repo-root.sh`**: A script to reliably locate the repository root.

---

## Root Level (Configuration & Rules)

The core configuration for the monorepo.

### Monorepo Management
- **`package.json`**: Defines workspaces (`react-sdk`, `showcase`, `docs`, `cli`, `packages/*`, `apps/*`) and shared dev dependencies.
- **`turbo.json`**: Configures Turborepo for optimized task execution (build, test, lint) and caching.
- **`package-lock.json`**: Locks dependencies for the entire monorepo.

### Environment & Deployment
- **`docker-compose.yml`**: Multi-container setup for running the full Tambo stack (API, DB, Web).
- **`docker.env.example`**: Example environment file for Docker deployments.
- **`conductor.json`**, **`conductor-setup.sh`**, **`conductor-run.sh`**: Configuration for the "Conductor" orchestration tool.
- **`mise.toml`**: Environment manager configuration (similar to asdf).

### Code Quality & Standards
- **`eslint.config.mjs`**: Shared ESLint configuration for the entire repository.
- **`prettierrc`**, **`.prettierignore`**: Shared formatting rules.
- **`lint-staged.config.mjs`**: Configures linting on files staged for commit.
- **`.node-version`**, **`.nvmrc`**: Standardizes the Node.js version.
- **`.cursorignore`**, **`.dockerignore`**, **`.gitignore`**: Files and directories to ignore in various contexts.

### Documentation & Guides
- **`README.md`**: The primary entry point for the repository.
- **`CONTRIBUTING.md`**: Guidelines for developers.
- **`LICENSE`**: MIT/Apache-2.0 license terms.
- **`RELEASING.md`**: Process for publishing new versions of the SDK and CLI.
- **`SELF-HOSTING.md`**: Instructions for self-hosting the Tambo platform.
- **`TOKENS.md`**: Documentation on authentication tokens and API keys.
- **`AGENTS.md`**, **`CLAUDE.md`**: Specialized instructions for AI agents working in this repository.
