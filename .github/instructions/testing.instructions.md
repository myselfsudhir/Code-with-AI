---
name: Testing standards
description: Unit, integration, contract, component and resilience testing.
applyTo: "**/src/test/**,**/*Test.java,**/*Tests.java,**/*IT.java"
---
# Testing standards
- Test observable behavior, not private implementation details.
- Use JUnit 5 and Mockito if already present; follow the project's existing test stack.
- Prefer real components for integration tests; use Testcontainers where useful and supported.
- Add tests for happy path, validation, boundary conditions, authorization, concurrency and failure paths.
- Test database migrations and repository behavior against the actual target database engine where practical.
- Test Kafka consumers for duplicate delivery, retries, ordering assumptions and poison messages.
- Avoid brittle tests that depend on wall-clock timing, random ports or external services.
- Use deterministic clocks, IDs and fixtures where appropriate.
- Do not mock the class under test.
- Do not weaken assertions or delete failing tests to make the suite pass.
- Report exactly which tests were run and whether they passed.
