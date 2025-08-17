---
url: "https://modelcontextprotocol.io/specification/2024-11-05/basic/index"
title: "Overview - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Version 2024-11-05

Search...

Ctrl K

Search...

Navigation

Base Protocol

Overview

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Protocol Layers](https://modelcontextprotocol.io/specification/2024-11-05/basic/index#protocol-layers)
- [Auth](https://modelcontextprotocol.io/specification/2024-11-05/basic/index#auth)
- [Schema](https://modelcontextprotocol.io/specification/2024-11-05/basic/index#schema)

**Protocol Revision**: 2024-11-05

All messages between MCP clients and servers **MUST** follow the
[JSON-RPC 2.0](https://www.jsonrpc.org/specification) specification. The protocol defines
three fundamental types of messages:

| Type | Description | Requirements |
| --- | --- | --- |
| `Requests` | Messages sent to initiate an operation | Must include unique ID and method name |
| `Responses` | Messages sent in reply to requests | Must include same ID as request |
| `Notifications` | One-way messages with no reply | Must not include an ID |

**Responses** are further sub-categorized as either **successful results** or **errors**.
Results can follow any JSON object structure, while errors must include an error code and
message at minimum.

## [​](https://modelcontextprotocol.io/specification/2024-11-05/basic/index\#protocol-layers)  Protocol Layers

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
support exactly the features they need.See the following pages for more details on the different components:

[**Lifecycle**](https://modelcontextprotocol.io/specification/2024-11-05/basic/lifecycle) [**Resources**](https://modelcontextprotocol.io/specification/2024-11-05/server/resources) [**Prompts**](https://modelcontextprotocol.io/specification/2024-11-05/server/prompts) [**Tools**](https://modelcontextprotocol.io/specification/2024-11-05/server/tools) [**Logging**](https://modelcontextprotocol.io/specification/2024-11-05/server/utilities/logging) [**Sampling**](https://modelcontextprotocol.io/specification/2024-11-05/client/sampling)

## [​](https://modelcontextprotocol.io/specification/2024-11-05/basic/index\#auth)  Auth

Authentication and authorization are not currently part of the core MCP specification,
but we are considering ways to introduce them in future. Join us in
[GitHub Discussions](https://github.com/modelcontextprotocol/specification/discussions)
to help shape the future of the protocol!Clients and servers **MAY** negotiate their own custom authentication and authorization
strategies.

## [​](https://modelcontextprotocol.io/specification/2024-11-05/basic/index\#schema)  Schema

The full specification of the protocol is defined as a
[TypeScript schema](http://github.com/modelcontextprotocol/specification/tree/main/schema/2024-11-05/schema.ts).
This is the source of truth for all protocol messages and structures.There is also a
[JSON Schema](http://github.com/modelcontextprotocol/specification/tree/main/schema/2024-11-05/schema.json),
which is automatically generated from the TypeScript source of truth, for use with
various automated tooling.

Was this page helpful?

YesNo

[Architecture](https://modelcontextprotocol.io/specification/2024-11-05/architecture/index) [Lifecycle](https://modelcontextprotocol.io/specification/2024-11-05/basic/lifecycle)

Assistant

Responses are generated using AI and may contain mistakes.