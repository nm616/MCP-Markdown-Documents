---
url: "https://modelcontextprotocol.io/specification/2024-11-05/server/tools"
title: "Tools - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Version 2024-11-05

Search...

Ctrl K

Search...

Navigation

Server Features

Tools

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [User Interaction Model](https://modelcontextprotocol.io/specification/2024-11-05/server/tools#user-interaction-model)
- [Capabilities](https://modelcontextprotocol.io/specification/2024-11-05/server/tools#capabilities)
- [Protocol Messages](https://modelcontextprotocol.io/specification/2024-11-05/server/tools#protocol-messages)
- [Listing Tools](https://modelcontextprotocol.io/specification/2024-11-05/server/tools#listing-tools)
- [Calling Tools](https://modelcontextprotocol.io/specification/2024-11-05/server/tools#calling-tools)
- [List Changed Notification](https://modelcontextprotocol.io/specification/2024-11-05/server/tools#list-changed-notification)
- [Message Flow](https://modelcontextprotocol.io/specification/2024-11-05/server/tools#message-flow)
- [Data Types](https://modelcontextprotocol.io/specification/2024-11-05/server/tools#data-types)
- [Tool](https://modelcontextprotocol.io/specification/2024-11-05/server/tools#tool)
- [Tool Result](https://modelcontextprotocol.io/specification/2024-11-05/server/tools#tool-result)
- [Text Content](https://modelcontextprotocol.io/specification/2024-11-05/server/tools#text-content)
- [Image Content](https://modelcontextprotocol.io/specification/2024-11-05/server/tools#image-content)
- [Embedded Resources](https://modelcontextprotocol.io/specification/2024-11-05/server/tools#embedded-resources)
- [Error Handling](https://modelcontextprotocol.io/specification/2024-11-05/server/tools#error-handling)
- [Security Considerations](https://modelcontextprotocol.io/specification/2024-11-05/server/tools#security-considerations)

**Protocol Revision**: 2024-11-05

The Model Context Protocol (MCP) allows servers to expose tools that can be invoked by
language models. Tools enable models to interact with external systems, such as querying
databases, calling APIs, or performing computations. Each tool is uniquely identified by
a name and includes metadata describing its schema.

## [​](https://modelcontextprotocol.io/specification/2024-11-05/server/tools\#user-interaction-model)  User Interaction Model

Tools in MCP are designed to be **model-controlled**, meaning that the language model can
discover and invoke tools automatically based on its contextual understanding and the
user’s prompts.However, implementations are free to expose tools through any interface pattern that
suits their needs—the protocol itself does not mandate any specific user
interaction model.

For trust & safety and security, there **SHOULD** always
be a human in the loop with the ability to deny tool invocations.Applications **SHOULD**:

- Provide UI that makes clear which tools are being exposed to the AI model
- Insert clear visual indicators when tools are invoked
- Present confirmation prompts to the user for operations, to ensure a human is in the
loop

## [​](https://modelcontextprotocol.io/specification/2024-11-05/server/tools\#capabilities)  Capabilities

Servers that support tools **MUST** declare the `tools` capability:

Copy

```
{
  "capabilities": {
    "tools": {
      "listChanged": true
    }
  }
}

```

`listChanged` indicates whether the server will emit notifications when the list of
available tools changes.

## [​](https://modelcontextprotocol.io/specification/2024-11-05/server/tools\#protocol-messages)  Protocol Messages

### [​](https://modelcontextprotocol.io/specification/2024-11-05/server/tools\#listing-tools)  Listing Tools

To discover available tools, clients send a `tools/list` request. This operation supports
[pagination](https://modelcontextprotocol.io/specification/2024-11-05/server/utilities/pagination).**Request:**

Copy

```
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "tools/list",
  "params": {
    "cursor": "optional-cursor-value"
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
    "tools": [\
      {\
        "name": "get_weather",\
        "description": "Get current weather information for a location",\
        "inputSchema": {\
          "type": "object",\
          "properties": {\
            "location": {\
              "type": "string",\
              "description": "City name or zip code"\
            }\
          },\
          "required": ["location"]\
        }\
      }\
    ],
    "nextCursor": "next-page-cursor"
  }
}

```

### [​](https://modelcontextprotocol.io/specification/2024-11-05/server/tools\#calling-tools)  Calling Tools

To invoke a tool, clients send a `tools/call` request:**Request:**

Copy

```
{
  "jsonrpc": "2.0",
  "id": 2,
  "method": "tools/call",
  "params": {
    "name": "get_weather",
    "arguments": {
      "location": "New York"
    }
  }
}

```

**Response:**

Copy

```
{
  "jsonrpc": "2.0",
  "id": 2,
  "result": {
    "content": [\
      {\
        "type": "text",\
        "text": "Current weather in New York:\nTemperature: 72°F\nConditions: Partly cloudy"\
      }\
    ],
    "isError": false
  }
}

```

### [​](https://modelcontextprotocol.io/specification/2024-11-05/server/tools\#list-changed-notification)  List Changed Notification

When the list of available tools changes, servers that declared the `listChanged`
capability **SHOULD** send a notification:

Copy

```
{
  "jsonrpc": "2.0",
  "method": "notifications/tools/list_changed"
}

```

## [​](https://modelcontextprotocol.io/specification/2024-11-05/server/tools\#message-flow)  Message Flow

ServerClientLLMServerClientLLMDiscoveryTool SelectionInvocationUpdatestools/listList of toolsSelect tool to usetools/callTool resultProcess resulttools/list\_changedtools/listUpdated tools

## [​](https://modelcontextprotocol.io/specification/2024-11-05/server/tools\#data-types)  Data Types

### [​](https://modelcontextprotocol.io/specification/2024-11-05/server/tools\#tool)  Tool

A tool definition includes:

- `name`: Unique identifier for the tool
- `description`: Human-readable description of functionality
- `inputSchema`: JSON Schema defining expected parameters

### [​](https://modelcontextprotocol.io/specification/2024-11-05/server/tools\#tool-result)  Tool Result

Tool results can contain multiple content items of different types:

#### [​](https://modelcontextprotocol.io/specification/2024-11-05/server/tools\#text-content)  Text Content

Copy

```
{
  "type": "text",
  "text": "Tool result text"
}

```

#### [​](https://modelcontextprotocol.io/specification/2024-11-05/server/tools\#image-content)  Image Content

Copy

```
{
  "type": "image",
  "data": "base64-encoded-data",
  "mimeType": "image/png"
}

```

#### [​](https://modelcontextprotocol.io/specification/2024-11-05/server/tools\#embedded-resources)  Embedded Resources

[Resources](https://modelcontextprotocol.io/specification/2024-11-05/server/resources) **MAY** be
embedded, to provide additional context or data, behind a URI that can be subscribed to
or fetched again by the client later:

Copy

```
{
  "type": "resource",
  "resource": {
    "uri": "resource://example",
    "mimeType": "text/plain",
    "text": "Resource content"
  }
}

```

## [​](https://modelcontextprotocol.io/specification/2024-11-05/server/tools\#error-handling)  Error Handling

Tools use two error reporting mechanisms:

1. **Protocol Errors**: Standard JSON-RPC errors for issues like:   - Unknown tools
   - Invalid arguments
   - Server errors
2. **Tool Execution Errors**: Reported in tool results with `isError: true`:   - API failures
   - Invalid input data
   - Business logic errors

Example protocol error:

Copy

```
{
  "jsonrpc": "2.0",
  "id": 3,
  "error": {
    "code": -32602,
    "message": "Unknown tool: invalid_tool_name"
  }
}

```

Example tool execution error:

Copy

```
{
  "jsonrpc": "2.0",
  "id": 4,
  "result": {
    "content": [\
      {\
        "type": "text",\
        "text": "Failed to fetch weather data: API rate limit exceeded"\
      }\
    ],
    "isError": true
  }
}

```

## [​](https://modelcontextprotocol.io/specification/2024-11-05/server/tools\#security-considerations)  Security Considerations

1. Servers **MUST**:   - Validate all tool inputs
   - Implement proper access controls
   - Rate limit tool invocations
   - Sanitize tool outputs
2. Clients **SHOULD**:   - Prompt for user confirmation on sensitive operations
   - Show tool inputs to the user before calling the server, to avoid malicious or
     accidental data exfiltration
   - Validate tool results before passing to LLM
   - Implement timeouts for tool calls
   - Log tool usage for audit purposes

Was this page helpful?

YesNo

[Resources](https://modelcontextprotocol.io/specification/2024-11-05/server/resources) [Completion](https://modelcontextprotocol.io/specification/2024-11-05/server/utilities/completion)

Assistant

Responses are generated using AI and may contain mistakes.