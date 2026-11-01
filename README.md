# Copilot Engineering Standards

A reusable GitHub Copilot customization starter kit for IntelliJ IDEA and Java 21 distributed systems.

## Technology baseline
- Java 21; Spring Boot 3.x/4.x only after checking compatibility of the chosen dependency set.
- Spring MVC/WebFlux only when justified; do not mix programming models casually.
- Spring Security, JWT resource-server patterns, API Gateway.
- Kafka for asynchronous messaging; Redis for caching/coordination only with explicit consistency and failure semantics.
- PostgreSQL and MySQL for relational persistence; MongoDB only where document access patterns justify it.
- Docker, Kubernetes, Actuator, Micrometer, OpenTelemetry, Prometheus and Grafana.

## Installation
1. Extract this archive into the root of your repository.
2. Open that repository in IntelliJ IDEA with GitHub Copilot enabled.
3. Keep `.github/copilot-instructions.md` as the primary always-on Copilot instruction file.
4. The additional `.instructions.md` files are organized by topic. JetBrains support for targeted instruction discovery can vary by Copilot plugin version; verify actual loading in Copilot Chat before relying on automatic `applyTo` behavior. If a file is not loaded automatically, reference/attach it in the chat or consolidate the relevant rule into `copilot-instructions.md`.
5. Open Copilot Chat's agent selector → Configure Agents to check whether the `.github/agents/*.agent.md` profiles are discovered.
6. Try prompt files from Copilot Chat using `/` and the prompt filename. Prompt-file support is preview and version-dependent in JetBrains.
7. Configure MCP servers through the IntelliJ Copilot MCP settings. Do not copy a server configuration from another IDE without checking its transport and schema.

## Important compatibility note
GitHub's customization feature matrix currently marks custom agents, prompt files and subagents as preview for JetBrains IDEs. Hooks are not supported in JetBrains in the current feature matrix. MCP servers are supported. Features and UI may change; consult the current GitHub Copilot customization cheat sheet.

## Recommended adoption order
1. Repository instructions and AGENTS.md.
2. One or two prompt files.
3. Backend and reviewer agents.
4. MCP integrations, starting read-only.
5. Remaining specialist agents and workflows.

## Safety
- Never give an AI agent production credentials, unrestricted shell access, or write access to production systems.
- Prefer read-only database and Kubernetes MCP accounts.
- Review diffs and commands before execution.
- Do not treat generated code, tests, documentation or citations as proof that a system is correct. Run verification.
