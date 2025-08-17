---
url: "https://modelcontextprotocol.io/specification/2025-06-18/basic"
title: "Overview - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Version 2025-06-18 (latest)

Search...

Ctrl K

Search...

Navigation

Base Protocol

Overview

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Messages](https://modelcontextprotocol.io/specification/2025-06-18/basic#messages)
- [Requests](https://modelcontextprotocol.io/specification/2025-06-18/basic#requests)
- [Responses](https://modelcontextprotocol.io/specification/2025-06-18/basic#responses)
- [Notifications](https://modelcontextprotocol.io/specification/2025-06-18/basic#notifications)
- [Auth](https://modelcontextprotocol.io/specification/2025-06-18/basic#auth)
- [Schema](https://modelcontextprotocol.io/specification/2025-06-18/basic#schema)
- [General fields](https://modelcontextprotocol.io/specification/2025-06-18/basic#general-fields)
- [\_meta](https://modelcontextprotocol.io/specification/2025-06-18/basic#meta)

**Protocol Revision**: 2025-06-18

The Model Context Protocol consists of several key components that work together:

- **Base Protocol**: Core JSON-RPC message types
- **Lifecycle Management**: Connection initialization, capability negotiation, and
session control
- **Authorization**: Authentication and authorization framework for HTTP-based transports
- **Server Features**: Resources, prompts, and tools exposed by servers
- **Client Features**: Sampling and root directory lists provided by clients
- **Utilities**: Cross-cutting concerns like logging and argument completion

All implementations **MUST** support the base protocol and lifecycle management
components. Other components **MAY** be implemented based on the specific needs of the
application.These protocol layers establish clear separation of concerns while enabling rich
interactions between clients and servers. The modular design allows implementations to
support exactly the features they need.

## [​](https://modelcontextprotocol.io/specification/2025-06-18/basic\#messages)  Messages

All messages between MCP clients and servers **MUST** follow the
[JSON-RPC 2.0](https://www.jsonrpc.org/specification) specification. The protocol defines
these types of messages:

### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic\#requests)  Requests

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

### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic\#responses)  Responses

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

### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic\#notifications)  Notifications

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

## [​](https://modelcontextprotocol.io/specification/2025-06-18/basic\#auth)  Auth

MCP provides an [Authorization](https://modelcontextprotocol.io/specification/2025-06-18/basic/authorization) framework for use with HTTP.
Implementations using an HTTP-based transport **SHOULD** conform to this specification,
whereas implementations using STDIO transport **SHOULD NOT** follow this specification,
and instead retrieve credentials from the environment.Additionally, clients and servers **MAY** negotiate their own custom authentication and
authorization strategies.For further discussions and contributions to the evolution of MCP’s auth mechanisms, join
us in
[GitHub Discussions](https://github.com/modelcontextprotocol/specification/discussions)
to help shape the future of the protocol!

## [​](https://modelcontextprotocol.io/specification/2025-06-18/basic\#schema)  Schema

The full specification of the protocol is defined as a
[TypeScript schema](https://github.com/modelcontextprotocol/specification/blob/main/schema/2025-06-18/schema.ts).
This is the source of truth for all protocol messages and structures.There is also a
[JSON Schema](https://github.com/modelcontextprotocol/specification/blob/main/schema/2025-06-18/schema.json),
which is automatically generated from the TypeScript source of truth, for use with
various automated tooling.

### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic\#general-fields)  General fields

#### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic\#meta)  `_meta`

The `_meta` property/parameter is reserved by MCP to allow clients and servers
to attach additional metadata to their interactions.Certain key names are reserved by MCP for protocol-level metadata, as specified below;
implementations MUST NOT make assumptions about values at these keys.Additionally, definitions in the [schema](https://github.com/modelcontextprotocol/specification/blob/main/schema/2025-06-18/schema.ts)
may reserve particular names for purpose-specific metadata, as declared in those definitions.**Key name format:** valid `_meta` key names have two segments: an optional **prefix**, and a **name**.**Prefix:**

- If specified, MUST be a series of labels separated by dots ( `.`), followed by a slash ( `/`).

  - Labels MUST start with a letter and end with a letter or digit; interior characters can be letters, digits, or hyphens ( `-`).
- Any prefix beginning with zero or more valid labels, followed by `modelcontextprotocol` or `mcp`, followed by any valid label,
is **reserved** for MCP use.

  - For example: `modelcontextprotocol.io/`, `mcp.dev/`, `api.modelcontextprotocol.org/`, and `tools.mcp.com/` are all reserved.

**Name:**

- Unless empty, MUST begin and end with an alphanumeric character ( `[a-z0-9A-Z]`).
- MAY contain hyphens ( `-`), underscores ( `_`), dots ( `.`), and alphanumerics in between.

Was this page helpful?

YesNo

[Architecture](https://modelcontextprotocol.io/specification/2025-06-18/architecture/index) [Lifecycle](https://modelcontextprotocol.io/specification/2025-06-18/basic/lifecycle)

Assistant

Responses are generated using AI and may contain mistakes.