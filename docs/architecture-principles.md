# Architecture Principles

## Service boundaries
- Organize services around business capabilities and bounded contexts.
- Each service owns its data and schema.
- Avoid shared database writes and distributed joins.
- Keep contracts explicit and versioned.

## Communication
- Use synchronous HTTP when the caller needs an immediate response and coupling is acceptable.
- Use Kafka when asynchronous processing, buffering, fan-out or temporal decoupling is valuable.
- Avoid long synchronous call chains.
- Set timeouts and define fallback behavior for every remote dependency.

## Data stores
- PostgreSQL or MySQL for relational transactions and constraints.
- MongoDB for document-shaped aggregates and flexible document queries when justified.
- Redis for cache, ephemeral coordination, rate limiting and short-lived state with explicit expiry.
- Select storage per service based on access patterns, consistency, operations and team expertise.

## API Gateway
- Route external traffic, apply edge policies and expose stable public APIs.
- Keep business authorization in the owning service.
- Avoid making the gateway a business-logic monolith.

## Security
- Validate JWTs using a supported resource-server implementation.
- Validate authorization at the resource/service boundary.
- Use least privilege, secret management, TLS and safe logging.

## Reliability
- Idempotency for retryable commands.
- Outbox/inbox for reliable state/event coordination.
- Bounded retry, jitter, timeout, circuit breaker and bulkhead where justified.
- Saga for cross-service workflows requiring compensation.
- Define data consistency and recovery semantics explicitly.

## Observability
- Structured logs with trace/correlation IDs.
- Metrics for latency, traffic, errors and saturation.
- Distributed traces across HTTP and Kafka.
- Health/readiness signals that reflect the service's ability to serve traffic.
