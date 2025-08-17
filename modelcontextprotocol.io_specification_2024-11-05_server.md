---
url: "https://modelcontextprotocol.io/specification/2024-11-05/server"
title: "Overview - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Version 2024-11-05

Search...

Ctrl K

Search...

Navigation

Server Features

Overview

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

**Protocol Revision**: 2024-11-05

Servers provide the fundamental building blocks for adding context to language models via
MCP. These primitives enable rich interactions between clients, servers, and language
models:

- **Prompts**: Pre-defined templates or instructions that guide language model
interactions
- **Resources**: Structured data or content that provides additional context to the model
- **Tools**: Executable functions that allow models to perform actions or retrieve
information

Each primitive can be summarized in the following control hierarchy:

| Primitive | Control | Description | Example |
| --- | --- | --- | --- |
| Prompts | User-controlled | Interactive templates invoked by user choice | Slash commands, menu options |
| Resources | Application-controlled | Contextual data attached and managed by the client | File contents, git history |
| Tools | Model-controlled | Functions exposed to the LLM to take actions | API POST requests, file writing |

Explore these key primitives in more detail below:

[**Prompts**](https://modelcontextprotocol.io/specification/2024-11-05/server/prompts) [**Resources**](https://modelcontextprotocol.io/specification/2024-11-05/server/resources) [**Tools**](https://modelcontextprotocol.io/specification/2024-11-05/server/tools)

Was this page helpful?

YesNo

[Sampling](https://modelcontextprotocol.io/specification/2024-11-05/client/sampling) [Prompts](https://modelcontextprotocol.io/specification/2024-11-05/server/prompts)

Assistant

Responses are generated using AI and may contain mistakes.