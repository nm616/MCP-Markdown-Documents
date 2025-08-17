---
url: "https://modelcontextprotocol.io/legacy/concepts/transports"
title: "Transports - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Search...

Ctrl K

Search...

Navigation

Transports

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Message Format](https://modelcontextprotocol.io/legacy/concepts/transports#message-format)
- [Requests](https://modelcontextprotocol.io/legacy/concepts/transports#requests)
- [Responses](https://modelcontextprotocol.io/legacy/concepts/transports#responses)
- [Notifications](https://modelcontextprotocol.io/legacy/concepts/transports#notifications)
- [Built-in Transport Types](https://modelcontextprotocol.io/legacy/concepts/transports#built-in-transport-types)
- [Standard Input/Output (stdio)](https://modelcontextprotocol.io/legacy/concepts/transports#standard-input%2Foutput-stdio)
- [Server](https://modelcontextprotocol.io/legacy/concepts/transports#server)
- [Client](https://modelcontextprotocol.io/legacy/concepts/transports#client)
- [Streamable HTTP](https://modelcontextprotocol.io/legacy/concepts/transports#streamable-http)
- [How it Works](https://modelcontextprotocol.io/legacy/concepts/transports#how-it-works)
- [Server](https://modelcontextprotocol.io/legacy/concepts/transports#server-2)
- [Client](https://modelcontextprotocol.io/legacy/concepts/transports#client-2)
- [Session Management](https://modelcontextprotocol.io/legacy/concepts/transports#session-management)
- [Resumability and Redelivery](https://modelcontextprotocol.io/legacy/concepts/transports#resumability-and-redelivery)
- [Security Considerations](https://modelcontextprotocol.io/legacy/concepts/transports#security-considerations)
- [Server-Sent Events (SSE) - Deprecated](https://modelcontextprotocol.io/legacy/concepts/transports#server-sent-events-sse-deprecated)
- [Legacy Security Considerations](https://modelcontextprotocol.io/legacy/concepts/transports#legacy-security-considerations)
- [Server](https://modelcontextprotocol.io/legacy/concepts/transports#server-3)
- [Client](https://modelcontextprotocol.io/legacy/concepts/transports#client-3)
- [Custom Transports](https://modelcontextprotocol.io/legacy/concepts/transports#custom-transports)
- [Error Handling](https://modelcontextprotocol.io/legacy/concepts/transports#error-handling)
- [Best Practices](https://modelcontextprotocol.io/legacy/concepts/transports#best-practices)
- [Security Considerations](https://modelcontextprotocol.io/legacy/concepts/transports#security-considerations-2)
- [Authentication and Authorization](https://modelcontextprotocol.io/legacy/concepts/transports#authentication-and-authorization)
- [Data Security](https://modelcontextprotocol.io/legacy/concepts/transports#data-security)
- [Network Security](https://modelcontextprotocol.io/legacy/concepts/transports#network-security)
- [Debugging Transport](https://modelcontextprotocol.io/legacy/concepts/transports#debugging-transport)
- [Backwards Compatibility](https://modelcontextprotocol.io/legacy/concepts/transports#backwards-compatibility)
- [For Servers Supporting Older Clients](https://modelcontextprotocol.io/legacy/concepts/transports#for-servers-supporting-older-clients)
- [For Clients Supporting Older Servers](https://modelcontextprotocol.io/legacy/concepts/transports#for-clients-supporting-older-servers)

Transports in the Model Context Protocol (MCP) provide the foundation for communication between clients and servers. A transport handles the underlying mechanics of how messages are sent and received.

## [​](https://modelcontextprotocol.io/legacy/concepts/transports\#message-format)  Message Format

MCP uses [JSON-RPC](https://www.jsonrpc.org/) 2.0 as its wire format. The transport layer is responsible for converting MCP protocol messages into JSON-RPC format for transmission and converting received JSON-RPC messages back into MCP protocol messages.There are three types of JSON-RPC messages used:

### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#requests)  Requests

Copy

```
{
  jsonrpc: "2.0",
  id: number | string,
  method: string,
  params?: object
}

```

### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#responses)  Responses

Copy

```
{
  jsonrpc: "2.0",
  id: number | string,
  result?: object,
  error?: {
    code: number,
    message: string,
    data?: unknown
  }
}

```

### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#notifications)  Notifications

Copy

```
{
  jsonrpc: "2.0",
  method: string,
  params?: object
}

```

## [​](https://modelcontextprotocol.io/legacy/concepts/transports\#built-in-transport-types)  Built-in Transport Types

MCP currently defines two standard transport mechanisms:

### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#standard-input%2Foutput-stdio)  Standard Input/Output (stdio)

The stdio transport enables communication through standard input and output streams. This is particularly useful for local integrations and command-line tools.Use stdio when:

- Building command-line tools
- Implementing local integrations
- Needing simple process communication
- Working with shell scripts

#### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#server)  Server

TypeScript

Python

Copy

```
const server = new Server(
  {
    name: "example-server",
    version: "1.0.0",
  },
  {
    capabilities: {},
  },
);

const transport = new StdioServerTransport();
await server.connect(transport);

```

#### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#client)  Client

TypeScript

Python

Copy

```
const client = new Client(
  {
    name: "example-client",
    version: "1.0.0",
  },
  {
    capabilities: {},
  },
);

const transport = new StdioClientTransport({
  command: "./server",
  args: ["--option", "value"],
});
await client.connect(transport);

```

### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#streamable-http)  Streamable HTTP

The Streamable HTTP transport uses HTTP POST requests for client-to-server communication and optional Server-Sent Events (SSE) streams for server-to-client communication.Use Streamable HTTP when:

- Building web-based integrations
- Needing client-server communication over HTTP
- Requiring stateful sessions
- Supporting multiple concurrent clients
- Implementing resumable connections

#### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#how-it-works)  How it Works

1. **Client-to-Server Communication**: Every JSON-RPC message from client to server is sent as a new HTTP POST request to the MCP endpoint
2. **Server Responses**: The server can respond either with:

   - A single JSON response ( `Content-Type: application/json`)
   - An SSE stream ( `Content-Type: text/event-stream`) for multiple messages
3. **Server-to-Client Communication**: Servers can send requests/notifications to clients via:

   - SSE streams initiated by client requests
   - SSE streams from HTTP GET requests to the MCP endpoint

#### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#server-2)  Server

TypeScript

Python

Copy

```
import express from "express";

const app = express();

const server = new Server(
  {
    name: "example-server",
    version: "1.0.0",
  },
  {
    capabilities: {},
  },
);

// MCP endpoint handles both POST and GET
app.post("/mcp", async (req, res) => {
  // Handle JSON-RPC request
  const response = await server.handleRequest(req.body);

  // Return single response or SSE stream
  if (needsStreaming) {
    res.setHeader("Content-Type", "text/event-stream");
    // Send SSE events...
  } else {
    res.json(response);
  }
});

app.get("/mcp", (req, res) => {
  // Optional: Support server-initiated SSE streams
  res.setHeader("Content-Type", "text/event-stream");
  // Send server notifications/requests...
});

app.listen(3000);

```

#### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#client-2)  Client

TypeScript

Python

Copy

```
const client = new Client(
  {
    name: "example-client",
    version: "1.0.0",
  },
  {
    capabilities: {},
  },
);

const transport = new HttpClientTransport(new URL("http://localhost:3000/mcp"));
await client.connect(transport);

```

#### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#session-management)  Session Management

Streamable HTTP supports stateful sessions to maintain context across multiple requests:

1. **Session Initialization**: Servers may assign a session ID during initialization by including it in an `Mcp-Session-Id` header
2. **Session Persistence**: Clients must include the session ID in all subsequent requests using the `Mcp-Session-Id` header
3. **Session Termination**: Sessions can be explicitly terminated by sending an HTTP DELETE request with the session ID

Example session flow:

Copy

```
// Server assigns session ID during initialization
app.post("/mcp", (req, res) => {
  if (req.body.method === "initialize") {
    const sessionId = generateSecureId();
    res.setHeader("Mcp-Session-Id", sessionId);
    // Store session state...
  }
  // Handle request...
});

// Client includes session ID in subsequent requests
fetch("/mcp", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    "Mcp-Session-Id": sessionId,
  },
  body: JSON.stringify(request),
});

```

#### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#resumability-and-redelivery)  Resumability and Redelivery

To support resuming broken connections, Streamable HTTP provides:

1. **Event IDs**: Servers can attach unique IDs to SSE events for tracking
2. **Resume from Last Event**: Clients can resume by sending the `Last-Event-ID` header
3. **Message Replay**: Servers can replay missed messages from the disconnection point

This ensures reliable message delivery even with unstable network connections.

#### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#security-considerations)  Security Considerations

When implementing Streamable HTTP transport, follow these security best practices:

1. **Validate Origin Headers**: Always validate the `Origin` header on all incoming connections to prevent DNS rebinding attacks
2. **Bind to Localhost**: When running locally, bind only to localhost (127.0.0.1) rather than all network interfaces (0.0.0.0)
3. **Implement Authentication**: Use proper authentication for all connections
4. **Use HTTPS**: Always use TLS/HTTPS for production deployments
5. **Validate Session IDs**: Ensure session IDs are cryptographically secure and properly validated

Without these protections, attackers could use DNS rebinding to interact with local MCP servers from remote websites.

### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#server-sent-events-sse-deprecated)  Server-Sent Events (SSE) - Deprecated

SSE as a standalone transport is deprecated as of protocol version 2024-11-05.
It has been replaced by Streamable HTTP, which incorporates SSE as an optional
streaming mechanism. For backwards compatibility information, see the
[backwards compatibility](https://modelcontextprotocol.io/legacy/concepts/transports#backwards-compatibility) section below.

The legacy SSE transport enabled server-to-client streaming with HTTP POST requests for client-to-server communication.Previously used when:

- Only server-to-client streaming is needed
- Working with restricted networks
- Implementing simple updates

#### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#legacy-security-considerations)  Legacy Security Considerations

The deprecated SSE transport had similar security considerations to Streamable HTTP, particularly regarding DNS rebinding attacks. These same protections should be applied when using SSE streams within the Streamable HTTP transport.

#### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#server-3)  Server

TypeScript

Python

Copy

```
import express from "express";

const app = express();

const server = new Server(
  {
    name: "example-server",
    version: "1.0.0",
  },
  {
    capabilities: {},
  },
);

let transport: SSEServerTransport | null = null;

app.get("/sse", (req, res) => {
  transport = new SSEServerTransport("/messages", res);
  server.connect(transport);
});

app.post("/messages", (req, res) => {
  if (transport) {
    transport.handlePostMessage(req, res);
  }
});

app.listen(3000);

```

#### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#client-3)  Client

TypeScript

Python

Copy

```
const client = new Client(
  {
    name: "example-client",
    version: "1.0.0",
  },
  {
    capabilities: {},
  },
);

const transport = new SSEClientTransport(new URL("http://localhost:3000/sse"));
await client.connect(transport);

```

## [​](https://modelcontextprotocol.io/legacy/concepts/transports\#custom-transports)  Custom Transports

MCP makes it easy to implement custom transports for specific needs. Any transport implementation just needs to conform to the Transport interface:You can implement custom transports for:

- Custom network protocols
- Specialized communication channels
- Integration with existing systems
- Performance optimization

TypeScript

Python

Copy

```
interface Transport {
  // Start processing messages
  start(): Promise<void>;

  // Send a JSON-RPC message
  send(message: JSONRPCMessage): Promise<void>;

  // Close the connection
  close(): Promise<void>;

  // Callbacks
  onclose?: () => void;
  onerror?: (error: Error) => void;
  onmessage?: (message: JSONRPCMessage) => void;
}

```

## [​](https://modelcontextprotocol.io/legacy/concepts/transports\#error-handling)  Error Handling

Transport implementations should handle various error scenarios:

1. Connection errors
2. Message parsing errors
3. Protocol errors
4. Network timeouts
5. Resource cleanup

Example error handling:

TypeScript

Python

Copy

```
class ExampleTransport implements Transport {
  async start() {
    try {
      // Connection logic
    } catch (error) {
      this.onerror?.(new Error(`Failed to connect: ${error}`));
      throw error;
    }
  }

  async send(message: JSONRPCMessage) {
    try {
      // Sending logic
    } catch (error) {
      this.onerror?.(new Error(`Failed to send message: ${error}`));
      throw error;
    }
  }
}

```

## [​](https://modelcontextprotocol.io/legacy/concepts/transports\#best-practices)  Best Practices

When implementing or using MCP transport:

01. Handle connection lifecycle properly
02. Implement proper error handling
03. Clean up resources on connection close
04. Use appropriate timeouts
05. Validate messages before sending
06. Log transport events for debugging
07. Implement reconnection logic when appropriate
08. Handle backpressure in message queues
09. Monitor connection health
10. Implement proper security measures

## [​](https://modelcontextprotocol.io/legacy/concepts/transports\#security-considerations-2)  Security Considerations

When implementing transport:

### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#authentication-and-authorization)  Authentication and Authorization

- Implement proper authentication mechanisms
- Validate client credentials
- Use secure token handling
- Implement authorization checks

### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#data-security)  Data Security

- Use TLS for network transport
- Encrypt sensitive data
- Validate message integrity
- Implement message size limits
- Sanitize input data

### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#network-security)  Network Security

- Implement rate limiting
- Use appropriate timeouts
- Handle denial of service scenarios
- Monitor for unusual patterns
- Implement proper firewall rules
- For HTTP-based transports (including Streamable HTTP), validate Origin headers to prevent DNS rebinding attacks
- For local servers, bind only to localhost (127.0.0.1) instead of all interfaces (0.0.0.0)

## [​](https://modelcontextprotocol.io/legacy/concepts/transports\#debugging-transport)  Debugging Transport

Tips for debugging transport issues:

01. Enable debug logging
02. Monitor message flow
03. Check connection states
04. Validate message formats
05. Test error scenarios
06. Use network analysis tools
07. Implement health checks
08. Monitor resource usage
09. Test edge cases
10. Use proper error tracking

## [​](https://modelcontextprotocol.io/legacy/concepts/transports\#backwards-compatibility)  Backwards Compatibility

To maintain compatibility between different protocol versions:

### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#for-servers-supporting-older-clients)  For Servers Supporting Older Clients

Servers wanting to support clients using the deprecated HTTP+SSE transport should:

1. Host both the old SSE and POST endpoints alongside the new MCP endpoint
2. Handle initialization requests on both endpoints
3. Maintain separate handling logic for each transport type

### [​](https://modelcontextprotocol.io/legacy/concepts/transports\#for-clients-supporting-older-servers)  For Clients Supporting Older Servers

Clients wanting to support servers using the deprecated transport should:

1. Accept server URLs that may use either transport
2. Attempt to POST an `InitializeRequest` with proper `Accept` headers:

   - If successful, use Streamable HTTP transport
   - If it fails with 4xx status, fall back to legacy SSE transport
3. Issue a GET request expecting an SSE stream with `endpoint` event for legacy servers

Example compatibility detection:

Copy

```
async function detectTransport(serverUrl: string): Promise<TransportType> {
  try {
    // Try Streamable HTTP first
    const response = await fetch(serverUrl, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        Accept: "application/json, text/event-stream",
      },
      body: JSON.stringify({
        jsonrpc: "2.0",
        method: "initialize",
        params: {
          /* ... */
        },
      }),
    });

    if (response.ok) {
      return "streamable-http";
    }
  } catch (error) {
    // Fall back to legacy SSE
    const sseResponse = await fetch(serverUrl, {
      method: "GET",
      headers: { Accept: "text/event-stream" },
    });

    if (sseResponse.ok) {
      return "legacy-sse";
    }
  }

  throw new Error("Unsupported transport");
}

```

Was this page helpful?

YesNo

Assistant

Responses are generated using AI and may contain mistakes.