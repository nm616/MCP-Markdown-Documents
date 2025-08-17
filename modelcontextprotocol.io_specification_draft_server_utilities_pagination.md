---
url: "https://modelcontextprotocol.io/specification/draft/server/utilities/pagination"
title: "Pagination - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Draft

Search...

Ctrl K

Search...

Navigation

Utilities

Pagination

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Pagination Model](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination#pagination-model)
- [Response Format](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination#response-format)
- [Request Format](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination#request-format)
- [Pagination Flow](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination#pagination-flow)
- [Operations Supporting Pagination](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination#operations-supporting-pagination)
- [Implementation Guidelines](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination#implementation-guidelines)
- [Error Handling](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination#error-handling)

**Protocol Revision**: draft

The Model Context Protocol (MCP) supports paginating list operations that may return
large result sets. Pagination allows servers to yield results in smaller chunks rather
than all at once.Pagination is especially important when connecting to external services over the
internet, but also useful for local integrations to avoid performance issues with large
data sets.

## [​](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination\#pagination-model)  Pagination Model

Pagination in MCP uses an opaque cursor-based approach, instead of numbered pages.

- The **cursor** is an opaque string token, representing a position in the result set
- **Page size** is determined by the server, and clients **MUST NOT** assume a fixed page
size

## [​](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination\#response-format)  Response Format

Pagination starts when the server sends a **response** that includes:

- The current page of results
- An optional `nextCursor` field if more results exist

Copy

```
{
  "jsonrpc": "2.0",
  "id": "123",
  "result": {
    "resources": [...],
    "nextCursor": "eyJwYWdlIjogM30="
  }
}

```

## [​](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination\#request-format)  Request Format

After receiving a cursor, the client can _continue_ paginating by issuing a request
including that cursor:

Copy

```
{
  "jsonrpc": "2.0",
  "method": "resources/list",
  "params": {
    "cursor": "eyJwYWdlIjogMn0="
  }
}

```

## [​](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination\#pagination-flow)  Pagination Flow

ServerClientServerClientloop\[Pagination Loop\]List Request (no cursor)Page of results + nextCursorList Request (with cursor)

## [​](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination\#operations-supporting-pagination)  Operations Supporting Pagination

The following MCP operations support pagination:

- `resources/list` \- List available resources
- `resources/templates/list` \- List resource templates
- `prompts/list` \- List available prompts
- `tools/list` \- List available tools

## [​](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination\#implementation-guidelines)  Implementation Guidelines

1. Servers **SHOULD**:   - Provide stable cursors
   - Handle invalid cursors gracefully
2. Clients **SHOULD**:   - Treat a missing `nextCursor` as the end of results
   - Support both paginated and non-paginated flows
3. Clients **MUST** treat cursors as opaque tokens:   - Don’t make assumptions about cursor format
   - Don’t attempt to parse or modify cursors
   - Don’t persist cursors across sessions

## [​](https://modelcontextprotocol.io/specification/draft/server/utilities/pagination\#error-handling)  Error Handling

Invalid cursors **SHOULD** result in an error with code -32602 (Invalid params).

Was this page helpful?

YesNo

[Logging](https://modelcontextprotocol.io/specification/draft/server/utilities/logging) [Schema Reference](https://modelcontextprotocol.io/specification/draft/schema)

Assistant

Responses are generated using AI and may contain mistakes.