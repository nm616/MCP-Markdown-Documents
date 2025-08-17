---
url: "https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging"
title: "Logging - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Version 2025-03-26

Search...

Ctrl K

Search...

Navigation

Utilities

Logging

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [User Interaction Model](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging#user-interaction-model)
- [Capabilities](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging#capabilities)
- [Log Levels](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging#log-levels)
- [Protocol Messages](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging#protocol-messages)
- [Setting Log Level](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging#setting-log-level)
- [Log Message Notifications](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging#log-message-notifications)
- [Message Flow](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging#message-flow)
- [Error Handling](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging#error-handling)
- [Implementation Considerations](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging#implementation-considerations)
- [Security](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging#security)

**Protocol Revision**: 2025-03-26

The Model Context Protocol (MCP) provides a standardized way for servers to send
structured log messages to clients. Clients can control logging verbosity by setting
minimum log levels, with servers sending notifications containing severity levels,
optional logger names, and arbitrary JSON-serializable data.

## [​](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging\#user-interaction-model)  User Interaction Model

Implementations are free to expose logging through any interface pattern that suits their
needs—the protocol itself does not mandate any specific user interaction model.

## [​](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging\#capabilities)  Capabilities

Servers that emit log message notifications **MUST** declare the `logging` capability:

Copy

```
{
  "capabilities": {
    "logging": {}
  }
}

```

## [​](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging\#log-levels)  Log Levels

The protocol follows the standard syslog severity levels specified in
[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424#section-6.2.1):

| Level | Description | Example Use Case |
| --- | --- | --- |
| debug | Detailed debugging information | Function entry/exit points |
| info | General informational messages | Operation progress updates |
| notice | Normal but significant events | Configuration changes |
| warning | Warning conditions | Deprecated feature usage |
| error | Error conditions | Operation failures |
| critical | Critical conditions | System component failures |
| alert | Action must be taken immediately | Data corruption detected |
| emergency | System is unusable | Complete system failure |

## [​](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging\#protocol-messages)  Protocol Messages

### [​](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging\#setting-log-level)  Setting Log Level

To configure the minimum log level, clients **MAY** send a `logging/setLevel` request:**Request:**

Copy

```
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "logging/setLevel",
  "params": {
    "level": "info"
  }
}

```

### [​](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging\#log-message-notifications)  Log Message Notifications

Servers send log messages using `notifications/message` notifications:

Copy

```
{
  "jsonrpc": "2.0",
  "method": "notifications/message",
  "params": {
    "level": "error",
    "logger": "database",
    "data": {
      "error": "Connection failed",
      "details": {
        "host": "localhost",
        "port": 5432
      }
    }
  }
}

```

## [​](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging\#message-flow)  Message Flow

ServerClientServerClientConfigure LoggingServer ActivityLevel ChangeOnly sends error leveland abovelogging/setLevel (info)Empty Resultnotifications/message (info)notifications/message (warning)notifications/message (error)logging/setLevel (error)Empty Result

## [​](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging\#error-handling)  Error Handling

Servers **SHOULD** return standard JSON-RPC errors for common failure cases:

- Invalid log level: `-32602` (Invalid params)
- Configuration errors: `-32603` (Internal error)

## [​](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging\#implementation-considerations)  Implementation Considerations

1. Servers **SHOULD**:   - Rate limit log messages
   - Include relevant context in data field
   - Use consistent logger names
   - Remove sensitive information
2. Clients **MAY**:   - Present log messages in the UI
   - Implement log filtering/search
   - Display severity visually
   - Persist log messages

## [​](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/logging\#security)  Security

1. Log messages **MUST NOT** contain:   - Credentials or secrets
   - Personal identifying information
   - Internal system details that could aid attacks
2. Implementations **SHOULD**:   - Rate limit messages
   - Validate all data fields
   - Control log access
   - Monitor for sensitive content

Was this page helpful?

YesNo

[Completion](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/completion) [Pagination](https://modelcontextprotocol.io/specification/2025-03-26/server/utilities/pagination)

Assistant

Responses are generated using AI and may contain mistakes.