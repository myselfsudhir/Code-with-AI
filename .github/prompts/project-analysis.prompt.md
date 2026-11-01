# Analyze this repository before development

Analyze the current repository for the task: ${input:task:What are we trying to build or change?}

Do not edit files.

1. Inspect the build files, modules, package structure, runtime configuration, tests, database migrations, API contracts, event contracts and deployment manifests relevant to the task.
2. Summarize only facts supported by inspected files.
3. Identify architecture, service boundaries, persistence technologies, messaging and security mechanisms actually present.
4. Identify missing information and contradictions.
5. List risks, dependencies and likely affected files.
6. Propose a minimal implementation plan and verification plan.

Separate **Observed**, **Assumed**, **Unknown** and **Recommended**. Do not invent classes, dependencies, versions, endpoints or runtime state.
