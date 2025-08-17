---
url: "https://modelcontextprotocol.io/specification/draft/server/tools"
title: "Tools - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Draft

Search...

Ctrl K

Search...

Navigation

Server Features

Tools

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [User Interaction Model](https://modelcontextprotocol.io/specification/draft/server/tools#user-interaction-model)
- [Capabilities](https://modelcontextprotocol.io/specification/draft/server/tools#capabilities)
- [Protocol Messages](https://modelcontextprotocol.io/specification/draft/server/tools#protocol-messages)
- [Listing Tools](https://modelcontextprotocol.io/specification/draft/server/tools#listing-tools)
- [Calling Tools](https://modelcontextprotocol.io/specification/draft/server/tools#calling-tools)
- [List Changed Notification](https://modelcontextprotocol.io/specification/draft/server/tools#list-changed-notification)
- [Message Flow](https://modelcontextprotocol.io/specification/draft/server/tools#message-flow)
- [Data Types](https://modelcontextprotocol.io/specification/draft/server/tools#data-types)
- [Tool](https://modelcontextprotocol.io/specification/draft/server/tools#tool)
- [Tool Result](https://modelcontextprotocol.io/specification/draft/server/tools#tool-result)
- [Text Content](https://modelcontextprotocol.io/specification/draft/server/tools#text-content)
- [Image Content](https://modelcontextprotocol.io/specification/draft/server/tools#image-content)
- [Audio Content](https://modelcontextprotocol.io/specification/draft/server/tools#audio-content)
- [Resource Links](https://modelcontextprotocol.io/specification/draft/server/tools#resource-links)
- [Embedded Resources](https://modelcontextprotocol.io/specification/draft/server/tools#embedded-resources)
- [Structured Content](https://modelcontextprotocol.io/specification/draft/server/tools#structured-content)
- [Output Schema](https://modelcontextprotocol.io/specification/draft/server/tools#output-schema)
- [Error Handling](https://modelcontextprotocol.io/specification/draft/server/tools#error-handling)
- [Security Considerations](https://modelcontextprotocol.io/specification/draft/server/tools#security-considerations)

**Protocol Revision**: draft

The Model Context Protocol (MCP) allows servers to expose tools that can be invoked by
language models. Tools enable models to interact with external systems, such as querying
databases, calling APIs, or performing computations. Each tool is uniquely identified by
a name and includes metadata describing its schema.

## [​](https://modelcontextprotocol.io/specification/draft/server/tools\#user-interaction-model)  User Interaction Model

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

## [​](https://modelcontextprotocol.io/specification/draft/server/tools\#capabilities)  Capabilities

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

## [​](https://modelcontextprotocol.io/specification/draft/server/tools\#protocol-messages)  Protocol Messages

### [​](https://modelcontextprotocol.io/specification/draft/server/tools\#listing-tools)  Listing Tools

To discover available tools, clients send a `tools/list` request. This operation supports
[pagination](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination).**Request:**

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
        "title": "Weather Information Provider",\
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

### [​](https://modelcontextprotocol.io/specification/draft/server/tools\#calling-tools)  Calling Tools

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

### [​](https://modelcontextprotocol.io/specification/draft/server/tools\#list-changed-notification)  List Changed Notification

When the list of available tools changes, servers that declared the `listChanged`
capability **SHOULD** send a notification:

Copy

```
{
  "jsonrpc": "2.0",
  "method": "notifications/tools/list_changed"
}

```

## [​](https://modelcontextprotocol.io/specification/draft/server/tools\#message-flow)  Message Flow

ServerClientLLMServerClientLLMDiscoveryTool SelectionInvocationUpdatestools/listList of toolsSelect tool to usetools/callTool resultProcess resulttools/list\_changedtools/listUpdated tools

## [​](https://modelcontextprotocol.io/specification/draft/server/tools\#data-types)  Data Types

### [​](https://modelcontextprotocol.io/specification/draft/server/tools\#tool)  Tool

A tool definition includes:

- `name`: Unique identifier for the tool
- `title`: Optional human-readable name of the tool for display purposes.
- `description`: Human-readable description of functionality
- `inputSchema`: JSON Schema defining expected parameters
- `outputSchema`: Optional JSON Schema defining expected output structure
- `annotations`: optional properties describing tool behavior

For trust & safety and security, clients **MUST** consider
tool annotations to be untrusted unless they come from trusted servers.

### [​](https://modelcontextprotocol.io/specification/draft/server/tools\#tool-result)  Tool Result

Tool results may contain [**structured**](https://modelcontextprotocol.io/specification/draft/server/tools#structured-content) or **unstructured** content.**Unstructured** content is returned in the `content` field of a result, and can contain multiple content items of different types:

All content types (text, image, audio, resource links, and embedded resources)
support optional
[annotations](https://modelcontextprotocol.io/specification/draft/server/resources#annotations) that provide
metadata about audience, priority, and modification times. This is the same
annotation format used by resources and prompts.

#### [​](https://modelcontextprotocol.io/specification/draft/server/tools\#text-content)  Text Content

Copy

```
{
  "type": "text",
  "text": "Tool result text"
}

```

#### [​](https://modelcontextprotocol.io/specification/draft/server/tools\#image-content)  Image Content

Copy

```
{
  "type": "image",
  "data": "base64-encoded-data",
  "mimeType": "image/png",
  "annotations": {
    "audience": ["user"],
    "priority": 0.9
  }
}

```

#### [​](https://modelcontextprotocol.io/specification/draft/server/tools\#audio-content)  Audio Content

Copy

```
{
  "type": "audio",
  "data": "base64-encoded-audio-data",
  "mimeType": "audio/wav"
}

```

#### [​](https://modelcontextprotocol.io/specification/draft/server/tools\#resource-links)  Resource Links

A tool **MAY** return links to [Resources](https://modelcontextprotocol.io/specification/draft/server/resources), to provide additional context
or data. In this case, the tool will return a URI that can be subscribed to or fetched by the client:

Copy

```
{
  "type": "resource_link",
  "uri": "file:///project/src/main.rs",
  "name": "main.rs",
  "description": "Primary application entry point",
  "mimeType": "text/x-rust"
}

```

Resource links support the same [Resource annotations](https://modelcontextprotocol.io/specification/draft/server/resources#annotations) as regular resources to help clients understand how to use them.

Resource links returned by tools are not guaranteed to appear in the results
of a `resources/list` request.

#### [​](https://modelcontextprotocol.io/specification/draft/server/tools\#embedded-resources)  Embedded Resources

[Resources](https://modelcontextprotocol.io/specification/draft/server/resources) **MAY** be embedded to provide additional context
or data using a suitable [URI scheme](https://modelcontextprotocol.io/specification/draft/server/resources#common-uri-schemes). Servers that use embedded resources **SHOULD** implement the `resources` capability:

Copy

```
{
  "type": "resource",
  "resource": {
    "uri": "file:///project/src/main.rs",
    "title": "Project Rust Main File",
    "mimeType": "text/x-rust",
    "text": "fn main() {\n    println!(\"Hello world!\");\n}",
    "annotations": {
      "audience": ["user", "assistant"],
      "priority": 0.7,
      "lastModified": "2025-05-03T14:30:00Z"
    }
  }
}

```

Embedded resources support the same [Resource annotations](https://modelcontextprotocol.io/specification/draft/server/resources#annotations) as regular resources to help clients understand how to use them.

#### [​](https://modelcontextprotocol.io/specification/draft/server/tools\#structured-content)  Structured Content

**Structured** content is returned as a JSON object in the `structuredContent` field of a result.For backwards compatibility, a tool that returns structured content SHOULD also return the serialized JSON in a TextContent block.

#### [​](https://modelcontextprotocol.io/specification/draft/server/tools\#output-schema)  Output Schema

Tools may also provide an output schema for validation of structured results.
If an output schema is provided:

- Servers **MUST** provide structured results that conform to this schema.
- Clients **SHOULD** validate structured results against this schema.

Example tool with output schema:

Copy

```
{
  "name": "get_weather_data",
  "title": "Weather Data Retriever",
  "description": "Get current weather data for a location",
  "inputSchema": {
    "type": "object",
    "properties": {
      "location": {
        "type": "string",
        "description": "City name or zip code"
      }
    },
    "required": ["location"]
  },
  "outputSchema": {
    "type": "object",
    "properties": {
      "temperature": {
        "type": "number",
        "description": "Temperature in celsius"
      },
      "conditions": {
        "type": "string",
        "description": "Weather conditions description"
      },
      "humidity": {
        "type": "number",
        "description": "Humidity percentage"
      }
    },
    "required": ["temperature", "conditions", "humidity"]
  }
}

```

Example valid response for this tool:

Copy

```
{
  "jsonrpc": "2.0",
  "id": 5,
  "result": {
    "content": [\
      {\
        "type": "text",\
        "text": "{\"temperature\": 22.5, \"conditions\": \"Partly cloudy\", \"humidity\": 65}"\
      }\
    ],
    "structuredContent": {
      "temperature": 22.5,
      "conditions": "Partly cloudy",
      "humidity": 65
    }
  }
}

```

Providing an output schema helps clients and LLMs understand and properly handle structured tool outputs by:

- Enabling strict schema validation of responses
- Providing type information for better integration with programming languages
- Guiding clients and LLMs to properly parse and utilize the returned data
- Supporting better documentation and developer experience

## [​](https://modelcontextprotocol.io/specification/draft/server/tools\#error-handling)  Error Handling

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

## [​](https://modelcontextprotocol.io/specification/draft/server/tools\#security-considerations)  Security Considerations

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

[Resources](https://modelcontextprotocol.io/specification/draft/server/resources) [Completion](https://modelcontextprotocol.io/specification/draft/server/utilities/completion)

Assistant

Responses are generated using AI and may contain mistakes.