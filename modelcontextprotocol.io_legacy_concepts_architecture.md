---
url: "https://modelcontextprotocol.io/legacy/concepts/architecture"
title: "Core architecture - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Search...

Ctrl K

Search...

Navigation

Core architecture

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Overview](https://modelcontextprotocol.io/legacy/concepts/architecture#overview)
- [Core components](https://modelcontextprotocol.io/legacy/concepts/architecture#core-components)
- [Protocol layer](https://modelcontextprotocol.io/legacy/concepts/architecture#protocol-layer)
- [Transport layer](https://modelcontextprotocol.io/legacy/concepts/architecture#transport-layer)
- [Message types](https://modelcontextprotocol.io/legacy/concepts/architecture#message-types)
- [Connection lifecycle](https://modelcontextprotocol.io/legacy/concepts/architecture#connection-lifecycle)
- [1\. Initialization](https://modelcontextprotocol.io/legacy/concepts/architecture#1-initialization)
- [2\. Message exchange](https://modelcontextprotocol.io/legacy/concepts/architecture#2-message-exchange)
- [3\. Termination](https://modelcontextprotocol.io/legacy/concepts/architecture#3-termination)
- [Error handling](https://modelcontextprotocol.io/legacy/concepts/architecture#error-handling)
- [Implementation example](https://modelcontextprotocol.io/legacy/concepts/architecture#implementation-example)
- [Best practices](https://modelcontextprotocol.io/legacy/concepts/architecture#best-practices)
- [Transport selection](https://modelcontextprotocol.io/legacy/concepts/architecture#transport-selection)
- [Message handling](https://modelcontextprotocol.io/legacy/concepts/architecture#message-handling)
- [Security considerations](https://modelcontextprotocol.io/legacy/concepts/architecture#security-considerations)
- [Debugging and monitoring](https://modelcontextprotocol.io/legacy/concepts/architecture#debugging-and-monitoring)

The Model Context Protocol (MCP) is built on a flexible, extensible architecture that enables seamless communication between LLM applications and integrations. This document covers the core architectural components and concepts.

## [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#overview)  Overview

MCP follows a client-server architecture where:

- **Hosts** are LLM applications (like Claude Desktop or IDEs) that initiate connections
- **Clients** maintain 1:1 connections with servers, inside the host application
- **Servers** provide context, tools, and prompts to clients

Server Process

Server Process

Host

Transport Layer

Transport Layer

MCP Client

MCP Client

MCP Server

MCP Server

## [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#core-components)  Core components

### [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#protocol-layer)  Protocol layer

The protocol layer handles message framing, request/response linking, and high-level communication patterns.

TypeScript

Python

Copy

```
class Protocol<Request, Notification, Result> {
  // Handle incoming requests
  setRequestHandler<T>(
    schema: T,
    handler: (request: T, extra: RequestHandlerExtra) => Promise<Result>,
  ): void;

  // Handle incoming notifications
  setNotificationHandler<T>(
    schema: T,
    handler: (notification: T) => Promise<void>,
  ): void;

  // Send requests and await responses
  request<T>(request: Request, schema: T, options?: RequestOptions): Promise<T>;

  // Send one-way notifications
  notification(notification: Notification): Promise<void>;
}

```

Key classes include:

- `Protocol`
- `Client`
- `Server`

### [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#transport-layer)  Transport layer

The transport layer handles the actual communication between clients and servers. MCP supports multiple transport mechanisms:

1. **Stdio transport**   - Uses standard input/output for communication
   - Ideal for local processes
2. **Streamable HTTP transport**   - Uses HTTP with optional Server-Sent Events for streaming
   - HTTP POST for client-to-server messages

All transports use [JSON-RPC](https://www.jsonrpc.org/) 2.0 to exchange messages. See the [specification](https://modelcontextprotocol.io/specification) for detailed information about the Model Context Protocol message format.

### [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#message-types)  Message types

MCP has these main types of messages:

1. **Requests** expect a response from the other side:






Copy











```
interface Request {
     method: string;
     params?: { ... };
}

```

2. **Results** are successful responses to requests:






Copy











```
interface Result {
     [key: string]: unknown;
}

```

3. **Errors** indicate that a request failed:






Copy











```
interface Error {
     code: number;
     message: string;
     data?: unknown;
}

```

4. **Notifications** are one-way messages that don’t expect a response:






Copy











```
interface Notification {
     method: string;
     params?: { ... };
}

```


## [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#connection-lifecycle)  Connection lifecycle

### [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#1-initialization)  1\. Initialization

ServerClientServerClientConnection ready for useinitialize requestinitialize responseinitialized notification

1. Client sends `initialize` request with protocol version and capabilities
2. Server responds with its protocol version and capabilities
3. Client sends `initialized` notification as acknowledgment
4. Normal message exchange begins

### [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#2-message-exchange)  2\. Message exchange

After initialization, the following patterns are supported:

- **Request-Response**: Client or server sends requests, the other responds
- **Notifications**: Either party sends one-way messages

### [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#3-termination)  3\. Termination

Either party can terminate the connection:

- Clean shutdown via `close()`
- Transport disconnection
- Error conditions

## [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#error-handling)  Error handling

MCP defines these standard error codes:

Copy

```
enum ErrorCode {
  // Standard JSON-RPC error codes
  ParseError = -32700,
  InvalidRequest = -32600,
  MethodNotFound = -32601,
  InvalidParams = -32602,
  InternalError = -32603,
}

```

SDKs and applications can define their own error codes above -32000.Errors are propagated through:

- Error responses to requests
- Error events on transports
- Protocol-level error handlers

## [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#implementation-example)  Implementation example

Here’s a basic example of implementing an MCP server:

TypeScript

Python

Copy

```
import { Server } from "@modelcontextprotocol/sdk/server/index.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";

const server = new Server(
  {
    name: "example-server",
    version: "1.0.0",
  },
  {
    capabilities: {
      resources: {},
    },
  },
);

// Handle requests
server.setRequestHandler(ListResourcesRequestSchema, async () => {
  return {
    resources: [\
      {\
        uri: "example://resource",\
        name: "Example Resource",\
      },\
    ],
  };
});

// Connect transport
const transport = new StdioServerTransport();
await server.connect(transport);

```

## [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#best-practices)  Best practices

### [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#transport-selection)  Transport selection

1. **Local communication**   - Use stdio transport for local processes
   - Efficient for same-machine communication
   - Simple process management
2. **Remote communication**   - Use Streamable HTTP for scenarios requiring HTTP compatibility
   - Consider security implications including authentication and authorization

### [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#message-handling)  Message handling

1. **Request processing**   - Validate inputs thoroughly
   - Use type-safe schemas
   - Handle errors gracefully
   - Implement timeouts
2. **Progress reporting**   - Use progress tokens for long operations
   - Report progress incrementally
   - Include total progress when known
3. **Error management**   - Use appropriate error codes
   - Include helpful error messages
   - Clean up resources on errors

## [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#security-considerations)  Security considerations

1. **Transport security**   - Use TLS for remote connections
   - Validate connection origins
   - Implement authentication when needed
2. **Message validation**   - Validate all incoming messages
   - Sanitize inputs
   - Check message size limits
   - Verify JSON-RPC format
3. **Resource protection**   - Implement access controls
   - Validate resource paths
   - Monitor resource usage
   - Rate limit requests
4. **Error handling**   - Don’t leak sensitive information
   - Log security-relevant errors
   - Implement proper cleanup
   - Handle DoS scenarios

## [​](https://modelcontextprotocol.io/legacy/concepts/architecture\#debugging-and-monitoring)  Debugging and monitoring

1. **Logging**   - Log protocol events
   - Track message flow
   - Monitor performance
   - Record errors
2. **Diagnostics**   - Implement health checks
   - Monitor connection state
   - Track resource usage
   - Profile performance
3. **Testing**   - Test different transports
   - Verify error handling
   - Check edge cases
   - Load test servers

Was this page helpful?

YesNo

Assistant

Responses are generated using AI and may contain mistakes.