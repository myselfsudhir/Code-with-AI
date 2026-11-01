# Repository Agent Guide

## Mission
Help build a maintainable, secure, observable distributed application using Java 21 and Spring Boot. Preserve the repository's existing architecture unless an approved change is required.

## Source of truth
1. Existing source code, tests, build files, migrations, OpenAPI specifications and deployment manifests.
2. Explicit architectural decisions in `docs/`.
3. `.github/copilot-instructions.md` and relevant topic instructions.
4. User-provided task requirements.
Never invent missing project facts. If sources conflict, report the conflict and ask before making a consequential choice.

## Before changing code
- Inspect the relevant module, package structure, build files, dependency versions, tests and configuration.
- Identify service boundaries, API/event contracts, persistence model and callers.
- State assumptions and unresolved questions.
- Produce a concise plan and list files expected to change.
- Do not create a new service, database, dependency, abstraction or design pattern without explaining why it is needed.

## Implementation standards
- Use Java 21 language features where they improve clarity; prefer records for immutable data carriers.
- Follow SOLID, clear separation of concerns and dependency inversion.
- Use constructor injection.
- Keep controllers thin; put business rules in application/domain services.
- Use DTOs at API boundaries; do not expose persistence entities.
- Validate untrusted input and enforce authorization server-side.
- Use explicit transaction boundaries.
- Design distributed operations for retries, duplicate delivery, partial failure and observability.
- Keep secrets out of source control and logs.

## Verification
- Add or update tests for changed behavior.
- Run the narrowest relevant test first, then broader tests where practical.
- Report exact commands run and their actual results.
- If a command was not run, say so. Never claim tests, builds, scans or deployments passed without evidence.
- Review the final diff for unrelated edits, secrets, unsafe defaults and missing tests.

## Hallucination control
- Do not fabricate classes, methods, endpoints, configuration keys, dependencies, annotations, framework behavior, database columns, event schemas or tool results.
- Inspect the repository or authoritative documentation before relying on a specific API.
- If uncertain, explicitly label the uncertainty and ask for the missing information.
- Separate observed facts, assumptions, recommendations and proposed changes.
- Do not silently substitute a different library or version.
