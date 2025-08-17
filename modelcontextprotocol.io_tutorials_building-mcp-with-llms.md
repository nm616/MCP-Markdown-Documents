---
url: "https://modelcontextprotocol.io/tutorials/building-mcp-with-llms"
title: "Building MCP with LLMs - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Search...

Ctrl K

Search...

Navigation

Building MCP with LLMs

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Preparing the documentation](https://modelcontextprotocol.io/tutorials/building-mcp-with-llms#preparing-the-documentation)
- [Describing your server](https://modelcontextprotocol.io/tutorials/building-mcp-with-llms#describing-your-server)
- [Working with Claude](https://modelcontextprotocol.io/tutorials/building-mcp-with-llms#working-with-claude)
- [Best practices](https://modelcontextprotocol.io/tutorials/building-mcp-with-llms#best-practices)
- [Next steps](https://modelcontextprotocol.io/tutorials/building-mcp-with-llms#next-steps)

This guide will help you use LLMs to help you build custom Model Context Protocol (MCP) servers and clients. We’ll be focusing on Claude for this tutorial, but you can do this with any frontier LLM.

## [​](https://modelcontextprotocol.io/tutorials/building-mcp-with-llms\#preparing-the-documentation)  Preparing the documentation

Before starting, gather the necessary documentation to help Claude understand MCP:

1. Visit [https://modelcontextprotocol.io/llms-full.txt](https://modelcontextprotocol.io/llms-full.txt) and copy the full documentation text
2. Navigate to either the [MCP TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk) or [Python SDK repository](https://github.com/modelcontextprotocol/python-sdk)
3. Copy the README files and other relevant documentation
4. Paste these documents into your conversation with Claude

## [​](https://modelcontextprotocol.io/tutorials/building-mcp-with-llms\#describing-your-server)  Describing your server

Once you’ve provided the documentation, clearly describe to Claude what kind of server you want to build. Be specific about:

- What resources your server will expose
- What tools it will provide
- Any prompts it should offer
- What external systems it needs to interact with

For example:

Copy

```
Build an MCP server that:
- Connects to my company's PostgreSQL database
- Exposes table schemas as resources
- Provides tools for running read-only SQL queries
- Includes prompts for common data analysis tasks

```

## [​](https://modelcontextprotocol.io/tutorials/building-mcp-with-llms\#working-with-claude)  Working with Claude

When working with Claude on MCP servers:

1. Start with the core functionality first, then iterate to add more features
2. Ask Claude to explain any parts of the code you don’t understand
3. Request modifications or improvements as needed
4. Have Claude help you test the server and handle edge cases

Claude can help implement all the key MCP features:

- Resource management and exposure
- Tool definitions and implementations
- Prompt templates and handlers
- Error handling and logging
- Connection and transport setup

## [​](https://modelcontextprotocol.io/tutorials/building-mcp-with-llms\#best-practices)  Best practices

When building MCP servers with Claude:

- Break down complex servers into smaller pieces
- Test each component thoroughly before moving on
- Keep security in mind - validate inputs and limit access appropriately
- Document your code well for future maintenance
- Follow MCP protocol specifications carefully

## [​](https://modelcontextprotocol.io/tutorials/building-mcp-with-llms\#next-steps)  Next steps

After Claude helps you build your server:

1. Review the generated code carefully
2. Test the server with the MCP Inspector tool
3. Connect it to Claude.app or other MCP clients
4. Iterate based on real usage and feedback

Remember that Claude can help you modify and improve your server as requirements change over time.Need more guidance? Just ask Claude specific questions about implementing MCP features or troubleshooting issues that arise.

Was this page helpful?

YesNo

Assistant

Responses are generated using AI and may contain mistakes.