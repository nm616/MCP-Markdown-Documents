---
url: "https://modelcontextprotocol.io/specification/2024-11-05/basic/transports"
title: "Transports - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Version 2024-11-05

Search...

Ctrl K

Search...

Navigation

Base Protocol

Transports

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [stdio](https://modelcontextprotocol.io/specification/2024-11-05/basic/transports#stdio)
- [HTTP with SSE](https://modelcontextprotocol.io/specification/2024-11-05/basic/transports#http-with-sse)
- [Security Warning](https://modelcontextprotocol.io/specification/2024-11-05/basic/transports#security-warning)
- [Custom Transports](https://modelcontextprotocol.io/specification/2024-11-05/basic/transports#custom-transports)

**Protocol Revision**: 2024-11-05

MCP currently defines two standard transport mechanisms for client-server communication:

1. [stdio](https://modelcontextprotocol.io/specification/2024-11-05/basic/transports#stdio), communication over standard in and standard out
2. [HTTP with Server-Sent Events](https://modelcontextprotocol.io/specification/2024-11-05/basic/transports#http-with-sse) (SSE)

Clients **SHOULD** support stdio whenever possible.It is also possible for clients and servers to implement
[custom transports](https://modelcontextprotocol.io/specification/2024-11-05/basic/transports#custom-transports) in a pluggable fashion.

## [​](https://modelcontextprotocol.io/specification/2024-11-05/basic/transports\#stdio)  stdio

In the **stdio** transport:

- The client launches the MCP server as a subprocess.
- The server receives JSON-RPC messages on its standard input ( `stdin`) and writes
responses to its standard output ( `stdout`).
- Messages are delimited by newlines, and **MUST NOT** contain embedded newlines.
- The server **MAY** write UTF-8 strings to its standard error ( `stderr`) for logging
purposes. Clients **MAY** capture, forward, or ignore this logging.
- The server **MUST NOT** write anything to its `stdout` that is not a valid MCP message.
- The client **MUST NOT** write anything to the server’s `stdin` that is not a valid MCP
message.

Server ProcessClientServer ProcessClientloop\[Message Exchange\]Launch subprocessWrite to stdinWrite to stdoutOptional logs on stderrClose stdin, terminate subprocess

## [​](https://modelcontextprotocol.io/specification/2024-11-05/basic/transports\#http-with-sse)  HTTP with SSE

In the **SSE** transport, the server operates as an independent process that can handle
multiple client connections.

#### [​](https://modelcontextprotocol.io/specification/2024-11-05/basic/transports\#security-warning)  Security Warning

When implementing HTTP with SSE transport:

1. Servers **MUST** validate the `Origin` header on all incoming connections to prevent DNS rebinding attacks
2. When running locally, servers **SHOULD** bind only to localhost (127.0.0.1) rather than all network interfaces (0.0.0.0)
3. Servers **SHOULD** implement proper authentication for all connections

Without these protections, attackers could use DNS rebinding to interact with local MCP servers from remote websites.The server **MUST** provide two endpoints:

1. An SSE endpoint, for clients to establish a connection and receive messages from the
server
2. A regular HTTP POST endpoint for clients to send messages to the server

When a client connects, the server **MUST** send an `endpoint` event containing a URI for
the client to use for sending messages. All subsequent client messages **MUST** be sent
as HTTP POST requests to this endpoint.Server messages are sent as SSE `message` events, with the message content encoded as
JSON in the event data.

ServerClientServerClientloop\[Message Exchange\]Open SSE connectionendpoint eventHTTP POST messagesSSE message eventsClose SSE connection

## [​](https://modelcontextprotocol.io/specification/2024-11-05/basic/transports\#custom-transports)  Custom Transports

Clients and servers **MAY** implement additional custom transport mechanisms to suit
their specific needs. The protocol is transport-agnostic and can be implemented over any
communication channel that supports bidirectional message exchange.Implementers who choose to support custom transports **MUST** ensure they preserve the
JSON-RPC message format and lifecycle requirements defined by MCP. Custom transports
**SHOULD** document their specific connection establishment and message exchange patterns
to aid interoperability.

Was this page helpful?

YesNo

[Messages](https://modelcontextprotocol.io/specification/2024-11-05/basic/messages) [Cancellation](https://modelcontextprotocol.io/specification/2024-11-05/basic/utilities/cancellation)

Assistant

Responses are generated using AI and may contain mistakes.