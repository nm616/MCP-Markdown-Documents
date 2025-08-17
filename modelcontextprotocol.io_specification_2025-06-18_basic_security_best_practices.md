---
url: "https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices"
title: "Security Best Practices - Model Context Protocol"
---

[Model Context Protocol home page![light logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/light.svg)![dark logo](https://mintlify.s3.us-west-1.amazonaws.com/mcp/logo/dark.svg)](https://modelcontextprotocol.io/)

Version 2025-06-18 (latest)

Search...

Ctrl K

Search...

Navigation

Base Protocol

Security Best Practices

[Documentation](https://modelcontextprotocol.io/docs/getting-started/intro) [Specification](https://modelcontextprotocol.io/specification/2025-06-18) [Community](https://modelcontextprotocol.io/community/communication) [About MCP](https://modelcontextprotocol.io/about)

On this page

- [Introduction](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#introduction)
- [Purpose and Scope](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#purpose-and-scope)
- [Attacks and Mitigations](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#attacks-and-mitigations)
- [Confused Deputy Problem](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#confused-deputy-problem)
- [Terminology](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#terminology)
- [Architecture and Attack Flows](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#architecture-and-attack-flows)
- [Attack Description](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#attack-description)
- [Mitigation](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#mitigation)
- [Token Passthrough](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#token-passthrough)
- [Risks](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#risks)
- [Mitigation](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#mitigation-2)
- [Session Hijacking](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#session-hijacking)
- [Session Hijack Prompt Injection](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#session-hijack-prompt-injection)
- [Session Hijack Impersonation](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#session-hijack-impersonation)
- [Attack Description](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#attack-description-2)
- [Mitigation](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices#mitigation-3)

## [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#introduction)  Introduction

### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#purpose-and-scope)  Purpose and Scope

This document provides security considerations for the Model Context Protocol (MCP), complementing the MCP Authorization specification. This document identifies security risks, attack vectors, and best practices specific to MCP implementations.The primary audience for this document includes developers implementing MCP authorization flows, MCP server operators, and security professionals evaluating MCP-based systems. This document should be read alongside the MCP Authorization specification and [OAuth 2.0 security best practices](https://datatracker.ietf.org/doc/html/rfc9700).

## [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#attacks-and-mitigations)  Attacks and Mitigations

This section gives a detailed description of attacks on MCP implementations, along with potential countermeasures.

### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#confused-deputy-problem)  Confused Deputy Problem

Attackers can exploit MCP servers proxying other resource servers, creating “ [confused deputy](https://en.wikipedia.org/wiki/Confused_deputy_problem)” vulnerabilities.

#### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#terminology)  Terminology

**MCP Proxy Server**
: An MCP server that connects MCP clients to third-party APIs, offering MCP features while delegating operations and acting as a single OAuth client to the third-party API server.**Third-Party Authorization Server**
: Authorization server that protects the third-party API. It may lack dynamic client registration support, requiring MCP proxy to use a static client ID for all requests.**Third-Party API**
: The protected resource server that provides the actual API functionality. Access to this
API requires tokens issued by the third-party authorization server.**Static Client ID**
: A fixed OAuth 2.0 client identifier used by the MCP proxy server when communicating with
the third-party authorization server. This Client ID refers to the MCP server acting as a client
to the Third-Party API. It is the same value for all MCP server to Third-Party API interactions regardless of
which MCP client initiated the request.

#### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#architecture-and-attack-flows)  Architecture and Attack Flows

##### Normal OAuth proxy usage (preserves user consent)

Third-Party Authorization ServerMCP Proxy ServerMCP ClientUser-Agent (Browser)Third-Party Authorization ServerMCP Proxy ServerMCP ClientUser-Agent (Browser)Initial Auth flow completedStep 1: Legitimate user consent for Third Party ServerReview consent screenExchange 3P code for 3P tokenGenerate MCP authorization codeExchange code for token, etc.Redirect to third party authorization serverAuthorization request (client\_id: mcp-proxy)Authorization consent screenApproveSet consent cookie for client ID: mcp-proxy3P Authorization code + redirect to mcp-proxy-server.com3P Authorization codeRedirect to MCP Client with MCP authorization code

##### Malicious OAuth proxy usage (skips user consent)

AttackerThird-Party Authorization ServerMCP Proxy ServerUser-Agent (Browser)AttackerThird-Party Authorization ServerMCP Proxy ServerUser-Agent (Browser)Step 2: Attack (leveraging existing cookie, skipping consent)Exchange 3P code for 3P tokenGenerate MCP authorization codeAttacker exchanges MCP code for MCP tokenDynamically register malicious client, redirect\_uri: attacker.comSends malicious linkAuthorization request (client\_id: mcp-proxy) + consent cookieCookie present, consent skipped3P Authorization code + redirect to mcp-proxy-server.com3P Authorization codeRedirect to attacker.com with MCP Authorization codeMCP Authorization code delivered to attacker.comAttacker impersonates user to MCP server

#### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#attack-description)  Attack Description

When an MCP proxy server uses a static client ID to authenticate with a third-party
authorization server that does not support dynamic client registration, the following
attack becomes possible:

1. A user authenticates normally through the MCP proxy server to access the third-party API
2. During this flow, the third-party authorization server sets a cookie on the user agent
indicating consent for the static client ID
3. An attacker later sends the user a malicious link containing a crafted authorization request which contains a malicious redirect URI along with a new dynamically registered client ID
4. When the user clicks the link, their browser still has the consent cookie from the previous legitimate request
5. The third-party authorization server detects the cookie and skips the consent screen
6. The MCP authorization code is redirected to the attacker’s server (specified in the crafted redirect\_uri during dynamic client registration)
7. The attacker exchanges the stolen authorization code for access tokens for the MCP server without the user’s explicit approval
8. Attacker now has access to the third-party API as the compromised user

#### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#mitigation)  Mitigation

MCP proxy servers using static client IDs **MUST** obtain user consent for each dynamically
registered client before forwarding to third-party authorization servers (which may require additional consent).

### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#token-passthrough)  Token Passthrough

“Token passthrough” is an anti-pattern where an MCP server accepts tokens from an MCP client without validating that the tokens were properly issued _to the MCP server_ and “passing them through” to the downstream API.

#### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#risks)  Risks

Token passthrough is explicitly forbidden in the [authorization specification](https://modelcontextprotocol.io/specification/2025-06-18/basic/authorization) as it introduces a number of security risks, that include:

- **Security Control Circumvention**
  - The MCP Server or downstream APIs might implement important security controls like rate limiting, request validation, or traffic monitoring, that depend on the token audience or other credential constraints. If clients can obtain and use tokens directly with the downstream APIs without the MCP server validating them properly or ensuring that the tokens are issued for the right service, they bypass these controls.
- **Accountability and Audit Trail Issues**
  - The MCP Server will be unable to identify or distinguish between MCP Clients when clients are calling with an upstream-issued access token which may be opaque to the MCP Server.
  - The downstream Resource Server’s logs may show requests that appear to come from a different source with a different identity, rather than the MCP server that is actually forwarding the tokens.
  - Both factors make incident investigation, controls, and auditing more difficult.
  - If the MCP Server passes tokens without validating their claims (e.g., roles, privileges, or audience) or other metadata, a malicious actor in possession of a stolen token can use the server as a proxy for data exfiltration.
- **Trust Boundary Issues**
  - The downstream Resource Server grants trust to specific entities. This trust might include assumptions about origin or client behavior patterns. Breaking this trust boundary could lead to unexpected issues.
  - If the token is accepted by multiple services without proper validation, an attacker compromising one service can use the token to access other connected services.
- **Future Compatibility Risk**
  - Even if an MCP Server starts as a “pure proxy” today, it might need to add security controls later. Starting with proper token audience separation makes it easier to evolve the security model.

#### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#mitigation-2)  Mitigation

MCP servers **MUST NOT** accept any tokens that were not explicitly issued for the MCP server.

### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#session-hijacking)  Session Hijacking

Session hijacking is an attack vector where a client is provided a session ID by the server, and an unauthorized party is able to obtain and use that same session ID to impersonate the original client and perform unauthorized actions on their behalf.

#### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#session-hijack-prompt-injection)  Session Hijack Prompt Injection

AttackerServerBQueueServerAClientAttackerServerBQueueServerAClientAttacker knows/guesses session IDInitialize (connect to streamable HTTP server)Respond with session IDAccess/guess session IDTrigger event (malicious payload, using session ID)Enqueue event (keyed by session ID)Poll for events (using session ID)Event data (malicious payload)Async response (malicious payload)Acts based on malicious payload

#### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#session-hijack-impersonation)  Session Hijack Impersonation

AttackerServerClientAttackerServerClientAttacker knows/guesses session IDInitialize (login/authenticate)Respond with session ID (persistent session created)Access/guess session IDMake API call (using session ID, no re-auth)Respond as if Attacker is Client (session hijack)

#### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#attack-description-2)  Attack Description

When you have multiple stateful HTTP servers that handle MCP requests, the following attack vectors are possible:**Session Hijack Prompt Injection**

1. The client connects to **Server A** and receives a session ID.
2. The attacker obtains an existing session ID and sends a malicious event to **Server B** with said session ID.   - When a server supports [redelivery/resumable streams](https://modelcontextprotocol.io/specification/2025-06-18/basic/transports#resumability-and-redelivery), deliberately terminating the request before receiving the response could lead to it being resumed by the original client via the GET request for server sent events.
   - If a particular server initiates server sent events as a consequence of a tool call such as a `notifications/tools/list_changed`, where it is possible to affect the tools that are offered by the server, a client could end up with tools that they were not aware were enabled.
3. **Server B** enqueues the event (associated with session ID) into a shared queue.
4. **Server A** polls the queue for events using the session ID and retrieves the malicious payload.
5. **Server A** sends the malicious payload to the client as an asynchronous or resumed response.
6. The client receives and acts on the malicious payload, leading to potential compromise.

**Session Hijack Impersonation**

1. The MCP client authenticates with the MCP server, creating a persistent session ID.
2. The attacker obtains the session ID.
3. The attacker makes calls to the MCP server using the session ID.
4. MCP server does not check for additional authorization and treats the attacker as a legitimate user, allowing unauthorized access or actions.

#### [​](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices\#mitigation-3)  Mitigation

To prevent session hijacking and event injection attacks, the following mitigations should be implemented:MCP servers that implement authorization **MUST** verify all inbound requests.
MCP Servers **MUST NOT** use sessions for authentication.MCP servers **MUST** use secure, non-deterministic session IDs.
Generated session IDs (e.g., UUIDs) **SHOULD** use secure random number generators. Avoid predictable or sequential session identifiers that could be guessed by an attacker. Rotating or expiring session IDs can also reduce the risk.MCP servers **SHOULD** bind session IDs to user-specific information.
When storing or transmitting session-related data (e.g., in a queue), combine the session ID with information unique to the authorized user, such as their internal user ID. Use a key format like `<user_id>:<session_id>`. This ensures that even if an attacker guesses a session ID, they cannot impersonate another user as the user ID is derived from the user token and not provided by the client.MCP servers can optionally leverage additional unique identifiers.

Was this page helpful?

YesNo

[Authorization](https://modelcontextprotocol.io/specification/2025-06-18/basic/authorization) [Cancellation](https://modelcontextprotocol.io/specification/2025-06-18/basic/utilities/cancellation)

Assistant

Responses are generated using AI and may contain mistakes.