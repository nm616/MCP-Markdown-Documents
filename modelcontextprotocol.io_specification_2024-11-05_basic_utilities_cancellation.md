---
url: "https://modelcontextprotocol.io/specification/2024-11-05/basic/utilities/cancellation"
title: "Cancellation - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Version 2024-11-05

Search...

Ctrl K

Search...

Navigation

Utilities

Cancellation

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Cancellation Flow](https://modelcontextprotocol.io/specification/2024-11-05/basic/utilities/cancellation#cancellation-flow)
- [Behavior Requirements](https://modelcontextprotocol.io/specification/2024-11-05/basic/utilities/cancellation#behavior-requirements)
- [Timing Considerations](https://modelcontextprotocol.io/specification/2024-11-05/basic/utilities/cancellation#timing-considerations)
- [Implementation Notes](https://modelcontextprotocol.io/specification/2024-11-05/basic/utilities/cancellation#implementation-notes)
- [Error Handling](https://modelcontextprotocol.io/specification/2024-11-05/basic/utilities/cancellation#error-handling)

**Protocol Revision**: 2024-11-05

The Model Context Protocol (MCP) supports optional cancellation of in-progress requests
through notification messages. Either side can send a cancellation notification to
indicate that a previously-issued request should be terminated.

## [​](https://modelcontextprotocol.io/specification/2024-11-05/basic/utilities/cancellation\#cancellation-flow)  Cancellation Flow

When a party wants to cancel an in-progress request, it sends a `notifications/cancelled`
notification containing:

- The ID of the request to cancel
- An optional reason string that can be logged or displayed

Copy

```
{
  "jsonrpc": "2.0",
  "method": "notifications/cancelled",
  "params": {
    "requestId": "123",
    "reason": "User requested cancellation"
  }
}

```

## [​](https://modelcontextprotocol.io/specification/2024-11-05/basic/utilities/cancellation\#behavior-requirements)  Behavior Requirements

1. Cancellation notifications **MUST** only reference requests that:

   - Were previously issued in the same direction
   - Are believed to still be in-progress
2. The `initialize` request **MUST NOT** be cancelled by clients
3. Receivers of cancellation notifications **SHOULD**:

   - Stop processing the cancelled request
   - Free associated resources
   - Not send a response for the cancelled request
4. Receivers **MAY** ignore cancellation notifications if:

   - The referenced request is unknown
   - Processing has already completed
   - The request cannot be cancelled
5. The sender of the cancellation notification **SHOULD** ignore any response to the
request that arrives afterward

## [​](https://modelcontextprotocol.io/specification/2024-11-05/basic/utilities/cancellation\#timing-considerations)  Timing Considerations

Due to network latency, cancellation notifications may arrive after request processing
has completed, and potentially after a response has already been sent.Both parties **MUST** handle these race conditions gracefully:

ServerClientServerClientProcessing startsProcessing may havecompleted beforecancellation arrivesStop processingalt​\[If notcompleted\]Request (ID: 123)notifications/cancelled (ID: 123)

## [​](https://modelcontextprotocol.io/specification/2024-11-05/basic/utilities/cancellation\#implementation-notes)  Implementation Notes

- Both parties **SHOULD** log cancellation reasons for debugging
- Application UIs **SHOULD** indicate when cancellation is requested

## [​](https://modelcontextprotocol.io/specification/2024-11-05/basic/utilities/cancellation\#error-handling)  Error Handling

Invalid cancellation notifications **SHOULD** be ignored:

- Unknown request IDs
- Already completed requests
- Malformed notifications

This maintains the “fire and forget” nature of notifications while allowing for race
conditions in asynchronous communication.

Was this page helpful?

YesNo

[Transports](https://modelcontextprotocol.io/specification/2024-11-05/basic/transports) [Ping](https://modelcontextprotocol.io/specification/2024-11-05/basic/utilities/ping)

Assistant

Responses are generated using AI and may contain mistakes.