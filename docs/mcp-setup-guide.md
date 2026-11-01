# MCP setup guide for IntelliJ + GitHub Copilot

MCP connects Copilot to external tools and data. Add only servers that solve a real workflow problem. MCP tools may read data or perform actions, so permissions and trust boundaries matter.

## Recommended staged setup

### Stage 1 — GitHub (if you work with GitHub-hosted repositories)
Use the official/verified GitHub MCP integration for repository, issue, pull request and workflow context. Start with read-only scopes. Enable write actions only when you explicitly need them.

### Stage 2 — Filesystem
Use a filesystem MCP server restricted to the project workspace. Prefer read-only access initially. Never expose your home directory, SSH keys, browser profiles, password stores or unrelated folders.

### Stage 3 — Database
Choose the database MCP server that matches the service you are actively working on:
- PostgreSQL read-only user for schema inspection and safe SELECT queries.
- MySQL read-only user for the same purpose.
- Do not connect both unless the project actually uses both.
- Do not expose production databases to a coding agent.
- Keep DDL/DML tools disabled initially.

### Stage 4 — Redis
Only add a Redis MCP server if you need to inspect local development cache keys, TTLs and values. Use a local disposable instance, restrict key patterns and avoid commands that mutate or flush data.

### Stage 5 — Kubernetes
Add a Kubernetes MCP integration only when actively debugging/developing deployments. Use a dedicated read-only RBAC identity and a non-production context. Do not grant delete, apply, patch, exec, secret-read or cluster-admin permissions by default.

### Optional — Documentation/search
A trusted documentation MCP server can help retrieve version-matched Spring, Java, Kafka or Kubernetes documentation. Prefer official documentation sources.

## Security checklist
- Verify publisher, source repository, package provenance and maintenance status.
- Read the server's tool list and understand every operation.
- Prefer read-only tools and least privilege.
- Use local/dev/test environments, never production by default.
- Do not put credentials directly in committed configuration.
- Use environment variables or the IDE's secure secret mechanism.
- Avoid broad filesystem roots and unrestricted shell tools.
- Confirm destructive operations manually.
- Review every tool call that writes, deploys, deletes or changes infrastructure.
- Treat MCP output as untrusted data; it may contain incorrect or malicious instructions.
- Remove servers you no longer use.

## IntelliJ configuration
Open Settings → Tools → GitHub Copilot → Model Context Protocol (MCP). Add the server using the transport and configuration format documented by that server and supported by your installed Copilot plugin. Do not assume the same JSON configuration path is shared by IntelliJ, VS Code and Copilot CLI.

After adding a server:
1. Inspect the tools exposed by it.
2. Confirm permissions and target environment.
3. Test a harmless read-only operation.
4. Ask Copilot to identify which MCP tool it used.
5. Confirm the result against the source system.

## Suggested starting set for this stack
Start with **Filesystem (workspace-only, read-only)** and **GitHub (read-only)**. Add one database MCP server for the database currently in use. Add Redis and Kubernetes only when you have a concrete workflow for them. Avoid installing five infrastructure MCP servers on day one.
