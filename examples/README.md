# Examples index (quick reference)

This file is a concise index of the example programs included in this repository. It summarizes the purpose of each example and links to the source under `src/examples/`.

If you want the longer narrative and diagrams, see `src/examples/README.md` which contains detailed background and deployment notes.

## Client examples

- `client/simpleStreamableHttp.ts` — Interactive command-line client for the Streamable HTTP transport. Demonstrates connecting, listing tools/prompts/resources, calling tools (including elicitation), handling notifications, resumability, and reading resources.
- `client/simpleOAuthClient.ts` — Interactive MCP client demonstrating the OAuth authorization flow: starts a temporary callback server, opens a browser for authorization, and connects using an authenticated Streamable HTTP transport.
- `client/streamableHttpWithSseFallbackClient.ts` — Backwards-compatible client that attempts Streamable HTTP first and falls back to the deprecated HTTP+SSE transport when needed. Useful for testing interoperability.
- `client/parallelToolCallsClient.ts` — Demonstrates launching multiple tool calls in parallel and tracking notifications per call.
- `client/multipleClientsParallel.ts` — Shows how to create multiple independent MCP clients in parallel, each calling tools and receiving notifications.

## Server examples

- `server/simpleStreamableHttp.ts` — Full Streamable HTTP server example implementing tools (`greet`, `multi-greet`, `collect-user-info`, `start-notification-stream`), prompts, resources, resumability (via `InMemoryEventStore`), and optional OAuth demo flags.
- `server/jsonResponseStreamableHttp.ts` — Streamable HTTP server configured to use JSON response mode (no SSE). Demonstrates servers that return results directly in the HTTP response.
- `server/standaloneSseWithGetStreamableHttp.ts` — Server showing server notifications and dynamic resource list changes; useful to test ResourceListChanged notifications.
- `server/simpleSseServer.ts` — Example of the deprecated HTTP+SSE transport (protocol 2024-11-05). Exposes `/mcp` for SSE and `/messages` for client POSTs; intended for backwards-compat testing.
- `server/sseAndStreamableHttpCompatibleServer.ts` — Backwards-compatible server exposing both Streamable HTTP and deprecated SSE endpoints. Demonstrates transport negotiation and session handling across protocols.
- `server/simpleStatelessStreamableHttp.ts` — Stateless Streamable HTTP server example (no session IDs). Good for stateless deployments or API-proxy style servers.
- `server/demoInMemoryOAuthProvider.ts` — Demo in-memory OAuth authorization provider used by OAuth examples; not for production but useful for local testing.
- `server/toolWithSampleServer.ts` — Example demonstrating use of the server's sampling/LLM APIs (implements a `summarize` tool that creates a sampled message).
- `server/mcpServerOutputSchema.ts` — Demonstrates defining tools with structured `outputSchema` and returning typed/structured results from tools.
- `server/resource-list-changed-notification-server.ts` — Example that dynamically creates resources and sends ResourceListChanged notifications to connected clients.

## Shared examples

- `shared/inMemoryEventStore.ts` — Small in-memory EventStore implementation used by server examples to demonstrate resumability and event replay. Intended for examples/tests, not production.

## Next steps (optional)

- I can add one-line "run" commands next to each example entry (e.g. `npx tsx src/examples/server/simpleStreamableHttp.ts`).
- I can also add small usage notes per example showing common command arguments or flags.

If you'd like those additions, tell me which format you prefer (inline run commands, separate table, or short usage blocks per file).
