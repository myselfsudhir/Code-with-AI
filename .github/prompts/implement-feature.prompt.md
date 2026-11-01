# Implement an approved feature

Feature: ${input:feature:Describe the approved feature}
Approved design/ADR: ${input:design:Reference the approved design or ADR}

First inspect the approved design and current implementation. Confirm the files and modules to change. Implement only the agreed scope.

Requirements:
- Java 21 and repository-compatible Spring Boot APIs.
- SOLID and existing architecture.
- Constructor injection and records for suitable immutable DTOs/events.
- DTO/entity separation, validation and global exception handling.
- Explicit local transaction boundaries.
- Secure authorization checks.
- Idempotency and failure handling for distributed operations.
- Tests for normal, boundary and failure paths.
- No invented dependencies, classes or configuration properties.
- No unrelated refactoring.

After implementation, inspect the diff and report changed files, tests actually run, exact results and remaining risks. If the design is incomplete, stop and ask.
