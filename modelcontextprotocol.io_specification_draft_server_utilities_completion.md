---
url: "https://modelcontextprotocol.io/specification/draft/server/utilities/completion"
title: "Completion - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Draft

Search...

Ctrl K

Search...

Navigation

Utilities

Completion

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [User Interaction Model](https://modelcontextprotocol.io/specification/draft/server/utilities/completion#user-interaction-model)
- [Capabilities](https://modelcontextprotocol.io/specification/draft/server/utilities/completion#capabilities)
- [Protocol Messages](https://modelcontextprotocol.io/specification/draft/server/utilities/completion#protocol-messages)
- [Requesting Completions](https://modelcontextprotocol.io/specification/draft/server/utilities/completion#requesting-completions)
- [Reference Types](https://modelcontextprotocol.io/specification/draft/server/utilities/completion#reference-types)
- [Completion Results](https://modelcontextprotocol.io/specification/draft/server/utilities/completion#completion-results)
- [Message Flow](https://modelcontextprotocol.io/specification/draft/server/utilities/completion#message-flow)
- [Data Types](https://modelcontextprotocol.io/specification/draft/server/utilities/completion#data-types)
- [CompleteRequest](https://modelcontextprotocol.io/specification/draft/server/utilities/completion#completerequest)
- [CompleteResult](https://modelcontextprotocol.io/specification/draft/server/utilities/completion#completeresult)
- [Error Handling](https://modelcontextprotocol.io/specification/draft/server/utilities/completion#error-handling)
- [Implementation Considerations](https://modelcontextprotocol.io/specification/draft/server/utilities/completion#implementation-considerations)
- [Security](https://modelcontextprotocol.io/specification/draft/server/utilities/completion#security)

**Protocol Revision**: draft

The Model Context Protocol (MCP) provides a standardized way for servers to offer
argument autocompletion suggestions for prompts and resource URIs. This enables rich,
IDE-like experiences where users receive contextual suggestions while entering argument
values.

## [​](https://modelcontextprotocol.io/specification/draft/server/utilities/completion\#user-interaction-model)  User Interaction Model

Completion in MCP is designed to support interactive user experiences similar to IDE code
completion.For example, applications may show completion suggestions in a dropdown or popup menu as
users type, with the ability to filter and select from available options.However, implementations are free to expose completion through any interface pattern that
suits their needs—the protocol itself does not mandate any specific user
interaction model.

## [​](https://modelcontextprotocol.io/specification/draft/server/utilities/completion\#capabilities)  Capabilities

Servers that support completions **MUST** declare the `completions` capability:

Copy

```
{
  "capabilities": {
    "completions": {}
  }
}

```

## [​](https://modelcontextprotocol.io/specification/draft/server/utilities/completion\#protocol-messages)  Protocol Messages

### [​](https://modelcontextprotocol.io/specification/draft/server/utilities/completion\#requesting-completions)  Requesting Completions

To get completion suggestions, clients send a `completion/complete` request specifying
what is being completed through a reference type:**Request:**

Copy

```
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "completion/complete",
  "params": {
    "ref": {
      "type": "ref/prompt",
      "name": "code_review"
    },
    "argument": {
      "name": "language",
      "value": "py"
    }
  }
}

```

**Response:**

Copy

```
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "completion": {
      "values": ["python", "pytorch", "pyside"],
      "total": 10,
      "hasMore": true
    }
  }
}

```

For prompts or URI templates with multiple arguments, clients should include previous completions in the `context.arguments` object to provide context for subsequent requests.**Request:**

Copy

```
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "completion/complete",
  "params": {
    "ref": {
      "type": "ref/prompt",
      "name": "code_review"
    },
    "argument": {
      "name": "framework",
      "value": "fla"
    },
    "context": {
      "arguments": {
        "language": "python"
      }
    }
  }
}

```

**Response:**

Copy

```
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "completion": {
      "values": ["flask"],
      "total": 1,
      "hasMore": false
    }
  }
}

```

### [​](https://modelcontextprotocol.io/specification/draft/server/utilities/completion\#reference-types)  Reference Types

The protocol supports two types of completion references:

| Type | Description | Example |
| --- | --- | --- |
| `ref/prompt` | References a prompt by name | `{"type": "ref/prompt", "name": "code_review"}` |
| `ref/resource` | References a resource URI | `{"type": "ref/resource", "uri": "file:///{path}"}` |

### [​](https://modelcontextprotocol.io/specification/draft/server/utilities/completion\#completion-results)  Completion Results

Servers return an array of completion values ranked by relevance, with:

- Maximum 100 items per response
- Optional total number of available matches
- Boolean indicating if additional results exist

## [​](https://modelcontextprotocol.io/specification/draft/server/utilities/completion\#message-flow)  Message Flow

ServerClientServerClientUser types argumentUser continues typingcompletion/completeCompletion suggestionscompletion/completeRefined suggestions

## [​](https://modelcontextprotocol.io/specification/draft/server/utilities/completion\#data-types)  Data Types

### [​](https://modelcontextprotocol.io/specification/draft/server/utilities/completion\#completerequest)  CompleteRequest

- `ref`: A `PromptReference` or `ResourceReference`
- `argument`: Object containing:

  - `name`: Argument name
  - `value`: Current value
- `context`: Object containing:

  - `arguments`: A mapping of already-resolved argument names to their values.

### [​](https://modelcontextprotocol.io/specification/draft/server/utilities/completion\#completeresult)  CompleteResult

- `completion`: Object containing:

  - `values`: Array of suggestions (max 100)
  - `total`: Optional total matches
  - `hasMore`: Additional results flag

## [​](https://modelcontextprotocol.io/specification/draft/server/utilities/completion\#error-handling)  Error Handling

Servers **SHOULD** return standard JSON-RPC errors for common failure cases:

- Method not found: `-32601` (Capability not supported)
- Invalid prompt name: `-32602` (Invalid params)
- Missing required arguments: `-32602` (Invalid params)
- Internal errors: `-32603` (Internal error)

## [​](https://modelcontextprotocol.io/specification/draft/server/utilities/completion\#implementation-considerations)  Implementation Considerations

1. Servers **SHOULD**:   - Return suggestions sorted by relevance
   - Implement fuzzy matching where appropriate
   - Rate limit completion requests
   - Validate all inputs
2. Clients **SHOULD**:   - Debounce rapid completion requests
   - Cache completion results where appropriate
   - Handle missing or partial results gracefully

## [​](https://modelcontextprotocol.io/specification/draft/server/utilities/completion\#security)  Security

Implementations **MUST**:

- Validate all completion inputs
- Implement appropriate rate limiting
- Control access to sensitive suggestions
- Prevent completion-based information disclosure

Was this page helpful?

YesNo

[Tools](https://modelcontextprotocol.io/specification/draft/server/tools) [Logging](https://modelcontextprotocol.io/specification/draft/server/utilities/logging)

Assistant

Responses are generated using AI and may contain mistakes.