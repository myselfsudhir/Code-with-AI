# Project-wide Copilot instructions

You are assisting with a production-oriented distributed system built primarily with Java 21 and Spring Boot.

## Required engineering behavior
- Understand the existing codebase before proposing or changing code.
- Treat repository source, build files, tests, migrations, OpenAPI/event schemas and deployment manifests as the source of truth.
- Follow `AGENTS.md` and the relevant topic guide in `.github/instructions/`. If a topic guide is not automatically loaded in this IDE version, ask the user to attach/reference it.
- Preserve established conventions unless there is a concrete reason to change them.
- Prefer the simplest design that satisfies functional, reliability, security and operational requirements.
- Apply SOLID principles pragmatically. Avoid speculative abstractions and unnecessary design patterns.
- Use Java 21. Use records for immutable request/response/event/value data where appropriate; do not use records for mutable JPA entities.
- Use constructor injection, explicit validation, DTO boundaries, centralized error handling and structured logs.
- Design APIs and events for compatibility, idempotency, retries, timeouts and partial failures.
- Use transactions only within a single service's local database boundary. Do not imply that `@Transactional` spans independent microservices.
- Do not assume Kafka provides exactly-once business effects. Design consumers to tolerate duplicate delivery.
- Do not use Redis as the sole source of truth for durable business data unless explicitly designed and justified.
- Never expose secrets, tokens, passwords, personal data or sensitive payloads in logs.

## Anti-hallucination protocol
1. Inspect relevant files before making claims about this repository.
2. Do not invent symbols, APIs, dependencies, configuration properties, versions, endpoints, schemas, migrations, test results or deployment state.
3. When a required fact is missing, ask a focused question or state a clearly marked assumption.
4. For framework-specific behavior, verify against the exact dependency version in the build and use official documentation when available.
5. Distinguish facts observed in code from recommendations and proposed designs.
6. Never claim a command was executed or succeeded unless its output confirms that.
7. Do not fabricate citations, documentation links, benchmark results or security guarantees.
8. Before implementation, provide a short plan. For broad changes, wait for approval before editing.
9. After implementation, list changed files, design decisions, tests actually run, test results and remaining risks.
10. If verification is blocked, state precisely what could not be verified.

## Change safety
- Do not perform destructive database, Git, filesystem, cloud or Kubernetes operations without explicit approval.
- Do not run production commands or access production data.
- Do not add dependencies without checking compatibility, maintenance status, license and necessity.
- Never disable authentication, authorization, TLS, validation or tests to make a build pass.
- Do not weaken tests merely to obtain a green build.

## Architecture defaults
- Prefer independently deployable services with clear business capabilities, not services split by technical layer.
- Use synchronous HTTP for request/response interactions where appropriate and Kafka for asynchronous events where decoupling is valuable.
- Use an API Gateway for edge routing and cross-cutting concerns; enforce authorization in services as well.
- Prefer PostgreSQL or MySQL for relational transactional data. Choose one per service based on requirements; do not share one schema across services by default.
- Use MongoDB only for document-centric workloads with justified access patterns.
- Use Redis for cache, ephemeral coordination or rate limiting with explicit TTL, invalidation and outage behavior.
- Use the outbox pattern when database state and event publication must be made reliable.
- Use observability: correlation/trace IDs, metrics, distributed tracing and structured logs.

## Required response format for engineering tasks
- Understanding and evidence
- Assumptions / questions
- Proposed design
- Files to change
- Implementation
- Verification (commands and actual results)
- Risks / follow-up work
