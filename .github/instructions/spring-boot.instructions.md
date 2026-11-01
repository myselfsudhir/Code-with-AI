---
name: Spring Boot standards
description: Spring Boot application structure, dependency injection, transactions and configuration.
applyTo: "**/src/main/**/*.java,**/src/test/**/*.java,**/pom.xml,**/build.gradle,**/build.gradle.kts"
---
# Spring Boot standards
- Inspect the exact Spring Boot and Spring Framework versions before using APIs or configuration properties.
- Use constructor injection; avoid field injection.
- Keep controllers focused on HTTP mapping, request validation and response mapping.
- Keep business rules in application/domain services; keep persistence concerns in repositories/adapters.
- Use request/response DTOs; never serialize JPA entities directly as public API contracts.
- Use Jakarta Bean Validation at inbound boundaries and meaningful domain validation for business invariants.
- Implement a consistent global exception strategy using `@RestControllerAdvice`; do not leak stack traces or internal details to clients.
- Use `ProblemDetail` only if compatible with the selected Spring version and API contract.
- Define transaction boundaries at application-service methods where a use case requires atomic local database work.
- Avoid remote HTTP or Kafka calls inside long-running database transactions.
- Do not assume a Spring transaction spans multiple services or databases.
- Externalize configuration; use typed `@ConfigurationProperties` for grouped application settings.
- Keep environment-specific secrets outside source control.
- Use profiles deliberately; do not hide production defaults in developer-only profiles.
- Use Actuator endpoints with appropriate exposure and access controls.
- Avoid circular dependencies and service-to-service calls through internal bean references.
- Add tests for success, validation failure, authorization failure and persistence failure.
