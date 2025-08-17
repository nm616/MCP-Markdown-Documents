---
url: "https://modelcontextprotocol.io/specification/versioning"
title: "Versioning - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Search...

Ctrl K

Search...

Navigation

Concepts

Versioning

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Revisions](https://modelcontextprotocol.io/specification/versioning#revisions)
- [Negotiation](https://modelcontextprotocol.io/specification/versioning#negotiation)

The Model Context Protocol uses string-based version identifiers following the format
`YYYY-MM-DD`, to indicate the last date backwards incompatible changes were made.

The protocol version will _not_ be incremented when the
protocol is updated, as long as the changes maintain backwards compatibility. This allows
for incremental improvements while preserving interoperability.

## [​](https://modelcontextprotocol.io/specification/versioning\#revisions)  Revisions

Revisions may be marked as:

- **Draft**: in-progress specifications, not yet ready for consumption.
- **Current**: the current protocol version, which is ready for use and may continue to
receive backwards compatible changes.
- **Final**: past, complete specifications that will not be changed.

The **current** protocol version is [**2025-06-18**](https://modelcontextprotocol.io/specification/2025-06-18).

## [​](https://modelcontextprotocol.io/specification/versioning\#negotiation)  Negotiation

Version negotiation happens during
[initialization](https://modelcontextprotocol.io/specification/2025-06-18/basic/lifecycle#initialization). Clients and
servers **MAY** support multiple protocol versions simultaneously, but they **MUST**
agree on a single version to use for the session.The protocol provides appropriate error handling if version negotiation fails, allowing
clients to gracefully terminate connections when they cannot find a version compatible
with the server.

Was this page helpful?

YesNo

[Client Concepts](https://modelcontextprotocol.io/docs/learn/client-concepts) [Connect to Remote MCP Servers](https://modelcontextprotocol.io/docs/tutorials/use-remote-mcp-server)

Assistant

Responses are generated using AI and may contain mistakes.