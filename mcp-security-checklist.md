# MCP adoption security checklist

For issue #3, this is a sign-off checklist to complete before connecting MCP servers to internal data.

## 1. Trust-boundary inventory

For each server, record:

- Host/client: Claude, ChatGPT, VS Code, Cursor, etc.
- Transport: stdio, local HTTP, remote HTTP/SSE, or other.
- Server owner: internal, SaaS vendor, third-party package, or community repo.
- Data reachable: files, databases, tickets, repos, chat, browser/session state, credentials, network destinations.
- Actions exposed: read-only lookup, write/update, code execution, browser/shell automation, deployment, spending, account admin.
- Human approval points for any write, execute, or external-send action.

Do not approve a server until its data sources and tool authority are explicit.

## 2. Authentication and authorization

- Prefer short-lived, scoped credentials over long-lived personal tokens.
- Store secrets outside prompts, chat transcripts, and repo history.
- Verify OAuth scopes match documented tool actions.
- Use separate credentials for read-only and write-capable workflows.
- Avoid broad admin tokens; prefer per-server service accounts.
- Test revocation and confirm the server fails closed.

Classify every tool as `read_public`, `read_internal`, `write_low_risk`, `write_high_risk`, or `execute`. Start pilots with read-only tools; require explicit human approval for `write_high_risk` and `execute`.

## 3. Data exposure and prompt-injection checks

Treat retrieved content as untrusted input. Review whether:

- A document, web page, issue, ticket, or row can instruct the model to call another tool.
- One server can read secrets that another server can exfiltrate by email, chat, comments, or network calls.
- Tool results are clearly separated from system/developer instructions.
- Logs, traces, screenshots, or exports retain private data.
- Responses or telemetry are sent to external services.

Default control: do not put sensitive read tools and external-send/write tools in the same profile without a documented business need and a human approval step.

## 4. Host/client comparison

For each MCP host, capture supported transports, local vs remote server support, tool-call approval UI, always-allow/deny controls, config storage, log retention, per-workspace policy, and enterprise/admin restrictions. Do not assume host behavior is identical just because the server speaks MCP.

## 5. Network, dependency, and audit controls

- Pin package versions where practical.
- Prefer official SDKs or actively maintained repositories.
- Review install scripts and post-install hooks.
- Document outbound network destinations.
- Run servers with the narrowest filesystem and network access that works.
- Log who used which server/tool and when, without logging secrets or full private documents.
- Define a fast disable path and credential rotation path.

## Sign-off template

```text
MCP server:
Host/client:
Owner:
Business purpose:
Transport:
Credentials/scopes:
Data reachable:
Tool categories approved:
Human approval required for:
External network destinations:
Logging location/retention:
Rollback/disable procedure:
Review date:
Approver:
```

## First-pilot recommendation

Use one local, read-only MCP server against non-production data. Do not combine internal-data reads with external messaging, browser automation, shell execution, or production writes until the team has reviewed real tool-call logs and confirmed the host approval flow is understandable.
