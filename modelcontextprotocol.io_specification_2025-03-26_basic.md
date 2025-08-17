---
url: "https://modelcontextprotocol.io/specification/2025-03-26/basic"
title: "Overview - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Version 2025-03-26

Search...

Ctrl K

Search...

Navigation

Base Protocol

Overview

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Messages](https://modelcontextprotocol.io/specification/2025-03-26/basic#messages)
- [Requests](https://modelcontextprotocol.io/specification/2025-03-26/basic#requests)
- [Responses](https://modelcontextprotocol.io/specification/2025-03-26/basic#responses)
- [Notifications](https://modelcontextprotocol.io/specification/2025-03-26/basic#notifications)
- [Batching](https://modelcontextprotocol.io/specification/2025-03-26/basic#batching)
- [Auth](https://modelcontextprotocol.io/specification/2025-03-26/basic#auth)
- [Schema](https://modelcontextprotocol.io/specification/2025-03-26/basic#schema)

**Protocol Revision**: 2025-03-26

The Model Context Protocol consists of several key components that work together:

- **Base Protocol**: Core JSON-RPC message types
- **Lifecycle Management**: Connection initialization, capability negotiation, and
session control
- **Server Features**: Resources, prompts, and tools exposed by servers
- **Client Features**: Sampling and root directory lists provided by clients
- **Utilities**: Cross-cutting concerns like logging and argument completion

All implementations **MUST** support the base protocol and lifecycle management
components. Other components **MAY** be implemented based on the specific needs of the
application.These protocol layers establish clear separation of concerns while enabling rich
interactions between clients and servers. The modular design allows implementations to
support exactly the features they need.

## [​](https://modelcontextprotocol.io/specification/2025-03-26/basic\#messages)  Messages

All messages between MCP clients and servers **MUST** follow the
[JSON-RPC 2.0](https://www.jsonrpc.org/specification) specification. The protocol defines
these types of messages:

### [​](https://modelcontextprotocol.io/specification/2025-03-26/basic\#requests)  Requests

Requests are sent from the client to the server or vice versa, to initiate an operation.

Copy

```
{
  jsonrpc: "2.0";
  id: string | number;
  method: string;
  params?: {
    [key: string]: unknown;
  };
}

```

- Requests **MUST** include a string or integer ID.
- Unlike base JSON-RPC, the ID **MUST NOT** be `null`.
- The request ID **MUST NOT** have been previously used by the requestor within the same
session.

### [​](https://modelcontextprotocol.io/specification/2025-03-26/basic\#responses)  Responses

Responses are sent in reply to requests, containing the result or error of the operation.

Copy

```
{
  jsonrpc: "2.0";
  id: string | number;
  result?: {
    [key: string]: unknown;
  }
  error?: {
    code: number;
    message: string;
    data?: unknown;
  }
}

```

- Responses **MUST** include the same ID as the request they correspond to.
- **Responses** are further sub-categorized as either **successful results** or
**errors**. Either a `result` or an `error` **MUST** be set. A response **MUST NOT**
set both.
- Results **MAY** follow any JSON object structure, while errors **MUST** include an
error code and message at minimum.
- Error codes **MUST** be integers.

### [​](https://modelcontextprotocol.io/specification/2025-03-26/basic\#notifications)  Notifications

Notifications are sent from the client to the server or vice versa, as a one-way message.
The receiver **MUST NOT** send a response.

Copy

```
{
  jsonrpc: "2.0";
  method: string;
  params?: {
    [key: string]: unknown;
  };
}

```

- Notifications **MUST NOT** include an ID.

### [​](https://modelcontextprotocol.io/specification/2025-03-26/basic\#batching)  Batching

JSON-RPC also defines a means to
[batch multiple requests and notifications](https://www.jsonrpc.org/specification#batch),
by sending them in an array. MCP implementations **MAY** support sending JSON-RPC
batches, but **MUST** support receiving JSON-RPC batches.

## [​](https://modelcontextprotocol.io/specification/2025-03-26/basic\#auth)  Auth

MCP provides an [Authorization](https://modelcontextprotocol.io/specification/2025-03-26/basic/authorization) framework for use with HTTP.
Implementations using an HTTP-based transport **SHOULD** conform to this specification,
whereas implementations using STDIO transport **SHOULD NOT** follow this specification,
and instead retrieve credentials from the environment.Additionally, clients and servers **MAY** negotiate their own custom authentication and
authorization strategies.For further discussions and contributions to the evolution of MCP’s auth mechanisms, join
us in
[GitHub Discussions](https://github.com/modelcontextprotocol/specification/discussions)
to help shape the future of the protocol!

## [​](https://modelcontextprotocol.io/specification/2025-03-26/basic\#schema)  Schema

The full specification of the protocol is defined as a
[TypeScript schema](https://github.com/modelcontextprotocol/specification/blob/main/schema/2025-03-26/schema.ts).
This is the source of truth for all protocol messages and structures.There is also a
[JSON Schema](https://github.com/modelcontextprotocol/specification/blob/main/schema/2025-03-26/schema.json),
which is automatically generated from the TypeScript source of truth, for use with
various automated tooling.

Was this page helpful?

YesNo

[Architecture](https://modelcontextprotocol.io/specification/2025-03-26/architecture/index) [Lifecycle](https://modelcontextprotocol.io/specification/2025-03-26/basic/lifecycle)

Assistant

Responses are generated using AI and may contain mistakes.