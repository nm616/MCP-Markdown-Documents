---
url: "https://modelcontextprotocol.io/specification/2024-11-05/basic/messages"
title: "Messages - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Version 2024-11-05

Search...

Ctrl K

Search...

Navigation

Base Protocol

Messages

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Requests](https://modelcontextprotocol.io/specification/2024-11-05/basic/messages#requests)
- [Responses](https://modelcontextprotocol.io/specification/2024-11-05/basic/messages#responses)
- [Notifications](https://modelcontextprotocol.io/specification/2024-11-05/basic/messages#notifications)

**Protocol Revision**: 2024-11-05

All messages in MCP **MUST** follow the
[JSON-RPC 2.0](https://www.jsonrpc.org/specification) specification. The protocol defines
three types of messages:

## [​](https://modelcontextprotocol.io/specification/2024-11-05/basic/messages\#requests)  Requests

Requests are sent from the client to the server or vice versa.

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

## [​](https://modelcontextprotocol.io/specification/2024-11-05/basic/messages\#responses)  Responses

Responses are sent in reply to requests.

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
- Either a `result` or an `error` **MUST** be set. A response **MUST NOT** set both.
- Error codes **MUST** be integers.

## [​](https://modelcontextprotocol.io/specification/2024-11-05/basic/messages\#notifications)  Notifications

Notifications are sent from the client to the server or vice versa. They do not expect a
response.

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

Was this page helpful?

YesNo

[Lifecycle](https://modelcontextprotocol.io/specification/2024-11-05/basic/lifecycle) [Transports](https://modelcontextprotocol.io/specification/2024-11-05/basic/transports)

Assistant

Responses are generated using AI and may contain mistakes.