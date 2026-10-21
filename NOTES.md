# MCP Adoption Notes

Notes for our 20-minute intro talk on the Model Context Protocol (MCP), compiled from live web research.

## What is MCP

The Model Context Protocol (MCP) is an open-source standard for connecting AI applications to external systems. Using MCP, AI applications like Claude or ChatGPT can connect to data sources (local files, databases), tools (search engines, calculators), and workflows (specialized prompts) — enabling them to access key information and perform tasks.

The mental model from the official docs: MCP is like a USB-C port for AI applications. Just as USB-C provides a standardized way to connect electronic devices, MCP provides a standardized way to connect AI applications to external systems.

MCP was introduced by Anthropic on November 25, 2024 as a new open standard for connecting AI assistants to the systems where data lives — content repositories, business tools, and development environments. Its aim is to help frontier models produce better, more relevant responses by replacing fragmented, bespoke integrations with a single universal protocol.

Core architecture:

- Developers either expose their data through MCP servers, or build AI applications (MCP clients) that connect to these servers.
- Pre-built MCP servers were shared at launch for popular enterprise systems including Google Drive, Slack, GitHub, Git, Postgres, and Puppeteer.
- Early adopters included Block and Apollo, plus development tools companies Zed, Replit, Codeium, and Sourcegraph.

Why MCP matters:

- Developers: reduces development time and complexity when building, or integrating with, an AI application or agent.
- AI applications/agents: access to an ecosystem of data sources, tools, and apps, which enhances capabilities and the end-user experience.
- End-users: more capable AI applications that can access user data and take actions on the user's behalf.

Broad ecosystem support: AI assistants like Claude and ChatGPT, and development tools like Visual Studio Code (Copilot Chat MCP servers), Cursor, and MCPJam all support MCP — build once, integrate everywhere.

## Official resources

- Official documentation: https://modelcontextprotocol.io (built with Mintlify; the main entry point for docs, specification, and quickstart).
- Introduction / "What is MCP" page: https://modelcontextprotocol.io/docs/2026-07-28/getting-started/intro
- Specification (latest version 2026-07-28): https://modelcontextprotocol.io/specification/2026-07-28
- Anthropic's launch announcement: https://www.anthropic.com/news/model-context-protocol (published Nov 25, 2024)
- Official GitHub organization: https://github.com/modelcontextprotocol

Notable repositories in the `modelcontextprotocol` organization:

- modelcontextprotocol/modelcontextprotocol — the MCP specification and official documentation repo (the main repository).
- modelcontextprotocol/servers — Model Context Protocol Servers: the open-source repository of MCP server implementations (the org's most-starred repo, ~91k stars).
- modelcontextprotocol/python-sdk — official Python SDK for MCP servers and clients.
- modelcontextprotocol/typescript-sdk — official TypeScript SDK for MCP servers and clients.
- modelcontextprotocol/java-sdk — official Java SDK (maintained in collaboration with Spring AI).
- modelcontextprotocol/kotlin-sdk — official Kotlin SDK (maintained in collaboration with JetBrains).
- modelcontextprotocol/csharp-sdk — official C# SDK (maintained in collaboration with Microsoft).
- modelcontextprotocol/go-sdk — official Go SDK (maintained in collaboration with Google).
- modelcontextprotocol/rust-sdk — official Rust SDK.
- modelcontextprotocol/swift-sdk — official Swift SDK.
- modelcontextprotocol/php-sdk — official PHP SDK (maintained in collaboration with The PHP Foundation).
- modelcontextprotocol/inspector — visual testing tool for MCP servers.
- modelcontextprotocol/registry — community-driven registry service for MCP servers.
- modelcontextprotocol/quickstart-resources — servers and clients from the MCP tutorials.

Creators (per the specification repo README and Anthropic's announcement): David Soria Parra (@dsp) and Justin Spahr-Summers (@jspahrsummers), at Anthropic.

## Follow-ups

- Evaluate MCP server examples — review the pre-built/reference servers in `modelcontextprotocol/servers` and pick candidates relevant to our stack.
- Draft MCP client integration spike — spike a client using the official SDK that matches our language.
- Security review of MCP adoption — work through the MCP security considerations before exposing any internal data.
- Compare MCP host applications — compare how Claude, ChatGPT, VS Code, Cursor, and other hosts support MCP.
