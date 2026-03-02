# Control Flow: The Lifecycle of a Message

This document details the end-to-end flow of a user message through the Tambo ecosystem, from the React UI to the LLM and back.

## 1. Message Submission (React SDK)
The flow begins in the developer's React application.
- **`TamboProvider`**: Wraps the app and provides context (API keys, components, tools).
- **`useTamboThreadInput()`**: Provides the `submit()` function. When called, it sends a `POST` request to the Tambo API (`apps/api/threads/messages`).
- **`TamboClient`**: Manages the network request and initiates a Server-Sent Events (SSE) connection to stream the response.

## 2. API Orchestration (Tambo API)
The Tambo API receives the request and starts the AI decision loop.
- **`ThreadsController`**: Receives the message and persists it to the database (`packages/db`).
- **`AiService`**: Calls `TamboBackend.run()` from `packages/backend`.
- **`TamboBackend`**: Initializes the conversation context, including previous messages and the developer's registered components and tools.

## 3. The Decision Loop (Tambo Backend)
The AI (OpenAI, Anthropic, etc.) processes the message and decides on the next action.
- **`DecisionLoopService`**: Sends the prompt (including system instructions from `packages/backend/src/prompt`) to the LLM provider.
- **LLM Output**: The LLM can choose to:
    - **Reply with text**: A standard chat response.
    - **Call a tool**: Execute a server-side function (e.g., fetch data from a database).
    - **Render a component**: Select a registered React component and provide its props.
    - **Call an MCP tool**: Execute a tool provided by a connected Model Context Protocol server.

## 4. Component Streaming (Tambo Backend)
If the AI decides to render a component, Tambo begins streaming its props in real-time.
- **`ComponentStreamingService`**: Converts the LLM's JSON output into a stream of AG-UI events.
- **`response-parsing.ts`**: Handles partial JSON chunks from the LLM, ensuring they are valid before streaming.

## 5. UI Rendering (React SDK)
The React application receives the SSE stream and updates the UI.
- **`StreamHandler`**: Listens to the SSE connection and parses incoming events.
- **`JsonPatch`**: Applies partial prop updates to the active component state.
- **`ComponentRenderer`**: Matches the component name to the developer's registered component and renders it with the streaming props.
- **`useTambo()`**: Updates the `messages` array, allowing the UI to display the AI's response (text or component) as it arrives.

## 6. Local Tool Execution (Optional)
If the LLM requests a local tool (browser-side), the SDK handles the execution.
- **`ToolExecutor`**: Calls the function defined in the developer's `TamboTool` metadata.
- **Result Submission**: The result of the local tool is sent back to the API to continue the decision loop.
