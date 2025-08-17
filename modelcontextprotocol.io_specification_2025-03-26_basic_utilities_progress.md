---
url: "https://modelcontextprotocol.io/specification/2025-03-26/basic/utilities/progress"
title: "Progress - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Version 2025-03-26

Search...

Ctrl K

Search...

Navigation

Utilities

Progress

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Progress Flow](https://modelcontextprotocol.io/specification/2025-03-26/basic/utilities/progress#progress-flow)
- [Behavior Requirements](https://modelcontextprotocol.io/specification/2025-03-26/basic/utilities/progress#behavior-requirements)
- [Implementation Notes](https://modelcontextprotocol.io/specification/2025-03-26/basic/utilities/progress#implementation-notes)

**Protocol Revision**: 2025-03-26

The Model Context Protocol (MCP) supports optional progress tracking for long-running
operations through notification messages. Either side can send progress notifications to
provide updates about operation status.

## [​](https://modelcontextprotocol.io/specification/2025-03-26/basic/utilities/progress\#progress-flow)  Progress Flow

When a party wants to _receive_ progress updates for a request, it includes a
`progressToken` in the request metadata.

- Progress tokens **MUST** be a string or integer value
- Progress tokens can be chosen by the sender using any means, but **MUST** be unique
across all active requests.

Copy

```
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "some_method",
  "params": {
    "_meta": {
      "progressToken": "abc123"
    }
  }
}

```

The receiver **MAY** then send progress notifications containing:

- The original progress token
- The current progress value so far
- An optional “total” value
- An optional “message” value

Copy

```
{
  "jsonrpc": "2.0",
  "method": "notifications/progress",
  "params": {
    "progressToken": "abc123",
    "progress": 50,
    "total": 100,
    "message": "Reticulating splines..."
  }
}

```

- The `progress` value **MUST** increase with each notification, even if the total is
unknown.
- The `progress` and the `total` values **MAY** be floating point.
- The `message` field **SHOULD** provide relevant human readable progress information.

## [​](https://modelcontextprotocol.io/specification/2025-03-26/basic/utilities/progress\#behavior-requirements)  Behavior Requirements

1. Progress notifications **MUST** only reference tokens that:   - Were provided in an active request
   - Are associated with an in-progress operation
2. Receivers of progress requests **MAY**:   - Choose not to send any progress notifications
   - Send notifications at whatever frequency they deem appropriate
   - Omit the total value if unknown

ReceiverSenderReceiverSenderRequest with progress tokenProgress updatesloop\[Progress Updates\]Operation completeMethod request with progressTokenProgress notification (0.2/1.0)Progress notification (0.6/1.0)Progress notification (1.0/1.0)Method response

## [​](https://modelcontextprotocol.io/specification/2025-03-26/basic/utilities/progress\#implementation-notes)  Implementation Notes

- Senders and receivers **SHOULD** track active progress tokens
- Both parties **SHOULD** implement rate limiting to prevent flooding
- Progress notifications **MUST** stop after completion

Was this page helpful?

YesNo

[Ping](https://modelcontextprotocol.io/specification/2025-03-26/basic/utilities/ping) [Roots](https://modelcontextprotocol.io/specification/2025-03-26/client/roots)

Assistant

Responses are generated using AI and may contain mistakes.