---
url: "https://modelcontextprotocol.io/development/roadmap"
title: "Roadmap - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Search...

Ctrl K

Search...

Navigation

Roadmap

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Agents](https://modelcontextprotocol.io/development/roadmap#agents)
- [Authentication and Security](https://modelcontextprotocol.io/development/roadmap#authentication-and-security)
- [Validation](https://modelcontextprotocol.io/development/roadmap#validation)
- [Registry](https://modelcontextprotocol.io/development/roadmap#registry)
- [Multimodality](https://modelcontextprotocol.io/development/roadmap#multimodality)
- [Get Involved](https://modelcontextprotocol.io/development/roadmap#get-involved)

Last updated: **2025-07-22**

The Model Context Protocol is rapidly evolving. This page outlines our current thinking on key priorities and direction for approximately **the next six months**, though these may change significantly as the project develops. To see what’s changed recently, check out the **[specification changelog](https://modelcontextprotocol.io/specification/2025-06-18/changelog)**.

The ideas presented here are not commitments—we may solve these challenges differently than described, or some may not materialize at all. This is also not an _exhaustive_ list; we may incorporate work that isn’t mentioned here.

We value community participation! Each section links to relevant discussions where you can learn more and contribute your thoughts.For a technical view of our standardization process, visit the [Standards Track](https://github.com/orgs/modelcontextprotocol/projects/2/views/2) on GitHub, which tracks how proposals progress toward inclusion in the official [MCP specification](https://spec.modelcontextprotocol.io/).

## [​](https://modelcontextprotocol.io/development/roadmap\#agents)  Agents

As MCP increasingly becomes part of agentic workflows, we’re focusing on key improvements:

- **Asynchronous Operations**: supporting long-running operations that may take extended periods, with resilient handling of disconnections and reconnections

## [​](https://modelcontextprotocol.io/development/roadmap\#authentication-and-security)  Authentication and Security

We’re evolving our authorization and security resources to improve user safety and provide a better developer experience:

- **Guides and Best Practices**: documenting specifics about deploying MCP securely in the form of guides and best practices to help developers avoid common pitfalls.
- **Alternatives to Dynamic Client Registration (DCR)**: exploring alternatives to DCR, attempting to address operational challenges while preserving a smooth user experience.
- **Fine-grained Authorization**: developing mechanisms and guidelines for primitive authorization for sensitive actions
- **Enterprise Managed Authorization**: adding the capability for enterprises to simplify MCP server authorization with the help of Single Sign-On (SSO)
- **Secure Authorization Elicitation**: enable developers to integrate secure authorization flows for downstream APIs outside the main MCP server authorization

## [​](https://modelcontextprotocol.io/development/roadmap\#validation)  Validation

To foster a robust developer ecosystem, we plan to invest in:

- **Reference Client Implementations**: demonstrating protocol features with high-quality AI applications
- **Reference Server Implementation**: showcasing authentication patterns and remote deployment best practices
- **Compliance Test Suites**: automated verification that clients, servers, and SDKs properly implement the specification

These tools will help developers confidently implement MCP while ensuring consistent behavior across the ecosystem.

## [​](https://modelcontextprotocol.io/development/roadmap\#registry)  Registry

For MCP to reach its full potential, we need streamlined ways to distribute and discover MCP servers.We plan to develop an [**MCP Registry**](https://github.com/orgs/modelcontextprotocol/discussions/159) that will enable centralized server discovery and metadata. This registry will primarily function as an API layer that third-party marketplaces and discovery services can build upon.

## [​](https://modelcontextprotocol.io/development/roadmap\#multimodality)  Multimodality

Supporting the full spectrum of AI capabilities in MCP, including:

- **Additional Modalities**: video and other media types
- **[Streaming](https://github.com/modelcontextprotocol/specification/issues/117)**: multipart, chunked messages, and bidirectional communication for interactive experiences

## [​](https://modelcontextprotocol.io/development/roadmap\#get-involved)  Get Involved

We welcome your contributions to MCP’s future! Join our [GitHub Discussions](https://github.com/orgs/modelcontextprotocol/discussions) to share ideas, provide feedback, or participate in the development process.

Was this page helpful?

YesNo

[SEP Guidelines](https://modelcontextprotocol.io/community/sep-guidelines) [Example Clients](https://modelcontextprotocol.io/clients)

Assistant

Responses are generated using AI and may contain mistakes.