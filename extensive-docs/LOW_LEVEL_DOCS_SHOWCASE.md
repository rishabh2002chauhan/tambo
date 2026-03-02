# Low Level Overview: Docs, Showcase & Plugins

Documentation of the code files within the `docs/`, `showcase/`, and `plugins/` directories.

## `docs/` (Official Documentation)

The source code for [docs.tambo.co](https://docs.tambo.co), built with Next.js and MDX.

### Content (`content/docs/`)
A collection of MDX files that make up the primary documentation pages.
- Organized by category (concepts, guides, reference, getting-started).

### Application Logic (`src/`)
- **`app/`**: Next.js App Router for the documentation site.
- **`components/`**: UI components for the documentation interface (Sidebar, Search, MDX layout).
- **`providers/`**: Context providers for site-wide functionality.
- **`lib/`**: Utilities for fetching and processing documentation content.
- **`mdx-components.tsx`**: Custom styling and behavior for MDX elements.

### Configuration
- **`next.config.mjs`**, **`source.config.ts`**: Configuration for the documentation engine (Fumadocs/Nextra).

---

## `showcase/` (Example Applications)

A collection of reference applications demonstrating Tambo AI in action.

### Templates (`src/app/`)
Contains various demo pages and templates:
- **`analytics-template/`**: AI-powered dashboard for data visualization.
- **`generative-ui/`**: Demonstrations of different generative UI components (Charts, Notes).

### Shared Logic (`src/lib/` & `src/components/`)
- **`lib/`**: Reusable utilities for the showcase apps.
- **`components/`**: Shared UI components used across the different templates.
- **`providers/`**: Global state and theme providers for the showcase.

---

## `plugins/` (Extensions)

The extension layer for the Tambo ecosystem.

### `plugins/tambo/`
- **`skills/`**: A collection of predefined "skills" that can be easily added to a Tambo project to extend AI capabilities.
- **`README.md`**: Instructions for developing and using plugins.
