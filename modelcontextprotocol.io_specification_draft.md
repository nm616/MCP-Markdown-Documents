---
url: "https://modelcontextprotocol.io/specification/draft"
title: "Specification - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Draft

Search...

Ctrl K

Search...

Navigation

Specification

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Overview](https://modelcontextprotocol.io/specification/draft#overview)
- [Key Details](https://modelcontextprotocol.io/specification/draft#key-details)
- [Base Protocol](https://modelcontextprotocol.io/specification/draft#base-protocol)
- [Features](https://modelcontextprotocol.io/specification/draft#features)
- [Additional Utilities](https://modelcontextprotocol.io/specification/draft#additional-utilities)
- [Security and Trust & Safety](https://modelcontextprotocol.io/specification/draft#security-and-trust-%26-safety)
- [Key Principles](https://modelcontextprotocol.io/specification/draft#key-principles)
- [Implementation Guidelines](https://modelcontextprotocol.io/specification/draft#implementation-guidelines)
- [Learn More](https://modelcontextprotocol.io/specification/draft#learn-more)

[Model Context Protocol](https://modelcontextprotocol.io/) (MCP) is an open protocol that
enables seamless integration between LLM applications and external data sources and
tools. Whether you’re building an AI-powered IDE, enhancing a chat interface, or creating
custom AI workflows, MCP provides a standardized way to connect LLMs with the context
they need.This specification defines the authoritative protocol requirements, based on the
TypeScript schema in
[schema.ts](https://github.com/modelcontextprotocol/specification/blob/main/schema/draft/schema.ts).For implementation guides and examples, visit
[modelcontextprotocol.io](https://modelcontextprotocol.io/).The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD
NOT”, “RECOMMENDED”, “NOT RECOMMENDED”, “MAY”, and “OPTIONAL” in this document are to be
interpreted as described in [BCP 14](https://datatracker.ietf.org/doc/html/bcp14)
\[ [RFC2119](https://datatracker.ietf.org/doc/html/rfc2119)\]
\[ [RFC8174](https://datatracker.ietf.org/doc/html/rfc8174)\] when, and only when, they
appear in all capitals, as shown here.

## [​](https://modelcontextprotocol.io/specification/draft\#overview)  Overview

MCP provides a standardized way for applications to:

- Share contextual information with language models
- Expose tools and capabilities to AI systems
- Build composable integrations and workflows

The protocol uses [JSON-RPC](https://www.jsonrpc.org/) 2.0 messages to establish
communication between:

- **Hosts**: LLM applications that initiate connections
- **Clients**: Connectors within the host application
- **Servers**: Services that provide context and capabilities

MCP takes some inspiration from the
[Language Server Protocol](https://microsoft.github.io/language-server-protocol/), which
standardizes how to add support for programming languages across a whole ecosystem of
development tools. In a similar way, MCP standardizes how to integrate additional context
and tools into the ecosystem of AI applications.

## [​](https://modelcontextprotocol.io/specification/draft\#key-details)  Key Details

### [​](https://modelcontextprotocol.io/specification/draft\#base-protocol)  Base Protocol

- [JSON-RPC](https://www.jsonrpc.org/) message format
- Stateful connections
- Server and client capability negotiation

### [​](https://modelcontextprotocol.io/specification/draft\#features)  Features

Servers offer any of the following features to clients:

- **Resources**: Context and data, for the user or the AI model to use
- **Prompts**: Templated messages and workflows for users
- **Tools**: Functions for the AI model to execute

Clients may offer the following features to servers:

- **Sampling**: Server-initiated agentic behaviors and recursive LLM interactions
- **Roots**: Server-initiated inquiries into URI or filesystem boundaries to operate in
- **Elicitation**: Server-initiated requests for additional information from users

### [​](https://modelcontextprotocol.io/specification/draft\#additional-utilities)  Additional Utilities

- Configuration
- Progress tracking
- Cancellation
- Error reporting
- Logging

## [​](https://modelcontextprotocol.io/specification/draft\#security-and-trust-%26-safety)  Security and Trust & Safety

The Model Context Protocol enables powerful capabilities through arbitrary data access
and code execution paths. With this power comes important security and trust
considerations that all implementors must carefully address.

### [​](https://modelcontextprotocol.io/specification/draft\#key-principles)  Key Principles

1. **User Consent and Control**   - Users must explicitly consent to and understand all data access and operations
   - Users must retain control over what data is shared and what actions are taken
   - Implementors should provide clear UIs for reviewing and authorizing activities
2. **Data Privacy**   - Hosts must obtain explicit user consent before exposing user data to servers
   - Hosts must not transmit resource data elsewhere without user consent
   - User data should be protected with appropriate access controls
3. **Tool Safety**   - Tools represent arbitrary code execution and must be treated with appropriate
        caution.
     - In particular, descriptions of tool behavior such as annotations should be
       considered untrusted, unless obtained from a trusted server.
   - Hosts must obtain explicit user consent before invoking any tool
   - Users should understand what each tool does before authorizing its use
4. **LLM Sampling Controls**   - Users must explicitly approve any LLM sampling requests
   - Users should control:
     - Whether sampling occurs at all
     - The actual prompt that will be sent
     - What results the server can see
   - The protocol intentionally limits server visibility into prompts

### [​](https://modelcontextprotocol.io/specification/draft\#implementation-guidelines)  Implementation Guidelines

While MCP itself cannot enforce these security principles at the protocol level,
implementors **SHOULD**:

1. Build robust consent and authorization flows into their applications
2. Provide clear documentation of security implications
3. Implement appropriate access controls and data protections
4. Follow security best practices in their integrations
5. Consider privacy implications in their feature designs

## [​](https://modelcontextprotocol.io/specification/draft\#learn-more)  Learn More

Explore the detailed specification for each protocol component:

[**Architecture**](https://modelcontextprotocol.io/specification/draft/architecture) [**Base Protocol**](https://modelcontextprotocol.io/specification/draft/basic) [**Server Features**](https://modelcontextprotocol.io/specification/draft/server) [**Client Features**](https://modelcontextprotocol.io/specification/draft/client) [**Contributing**](https://modelcontextprotocol.io/development/contributing)

Was this page helpful?

YesNo

[Key Changes](https://modelcontextprotocol.io/specification/draft/changelog)

Assistant

Responses are generated using AI and may contain mistakes.