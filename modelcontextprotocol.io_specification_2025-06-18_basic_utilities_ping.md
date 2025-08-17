---
url: "https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/ping"
title: "Ping - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Version 2025-06-18 (latest)

Search...

Ctrl K

Search...

Navigation

Utilities

Ping

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Overview](https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/ping#overview)
- [Message Format](https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/ping#message-format)
- [Behavior Requirements](https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/ping#behavior-requirements)
- [Usage Patterns](https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/ping#usage-patterns)
- [Implementation Considerations](https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/ping#implementation-considerations)
- [Error Handling](https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/ping#error-handling)

**Protocol Revision**: 2025-06-18

The Model Context Protocol includes an optional ping mechanism that allows either party
to verify that their counterpart is still responsive and the connection is alive.

## [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/ping\#overview)  Overview

The ping functionality is implemented through a simple request/response pattern. Either
the client or server can initiate a ping by sending a `ping` request.

## [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/ping\#message-format)  Message Format

A ping request is a standard JSON-RPC request with no parameters:

Copy

```
{
  "jsonrpc": "2.0",
  "id": "123",
  "method": "ping"
}

```

## [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/ping\#behavior-requirements)  Behavior Requirements

1. The receiver **MUST** respond promptly with an empty response:

Copy

```
{
  "jsonrpc": "2.0",
  "id": "123",
  "result": {}
}

```

2. If no response is received within a reasonable timeout period, the sender **MAY**:

   - Consider the connection stale
   - Terminate the connection
   - Attempt reconnection procedures

## [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/ping\#usage-patterns)  Usage Patterns

ReceiverSenderReceiverSenderping requestempty response

## [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/ping\#implementation-considerations)  Implementation Considerations

- Implementations **SHOULD** periodically issue pings to detect connection health
- The frequency of pings **SHOULD** be configurable
- Timeouts **SHOULD** be appropriate for the network environment
- Excessive pinging **SHOULD** be avoided to reduce network overhead

## [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/ping\#error-handling)  Error Handling

- Timeouts **SHOULD** be treated as connection failures
- Multiple failed pings **MAY** trigger connection reset
- Implementations **SHOULD** log ping failures for diagnostics

Was this page helpful?

YesNo

[Cancellation](https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/cancellation) [Progress](https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/progress)

Assistant

Responses are generated using AI and may contain mistakes.