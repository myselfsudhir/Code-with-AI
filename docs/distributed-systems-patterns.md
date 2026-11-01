# Distributed Systems Reliability Patterns

## Idempotency
Define a stable idempotency key, scope, persistence location, request fingerprint, expiry, concurrent request behavior and replay response. A unique database constraint is often needed to prevent races. Never assume a cache-only key provides durable protection.

## Transactional Outbox
Write business state and an outbox record in the same local database transaction. A separate publisher sends outbox records to Kafka and marks them delivered. Design for publisher retries and duplicate publication; consumers should still be idempotent.

## Inbox / Idempotent Consumer
Persist a processed-message identity with the business effect in one local transaction where possible. Use a uniqueness constraint to handle concurrent duplicate deliveries.

## Saga
Model each step, success transition, compensation, timeout, retry and terminal/manual-recovery state. Compensation is a new business action, not a database rollback across services.

## Retry
Retry only transient faults. Bound attempts, use exponential backoff with jitter, and respect deadlines. Avoid retrying non-idempotent operations without an idempotency strategy.

## Circuit Breaker and Bulkhead
Use measured thresholds and separate resource pools where justified. Define half-open behavior and fallback semantics. Do not use a circuit breaker as a substitute for timeouts.

## Kafka ordering and delivery
Ordering is per partition. Choose message keys to preserve required aggregate ordering. Assume duplicate delivery and design consumer effects accordingly.

## Observability
Propagate trace context across HTTP and messaging. Record event IDs, correlation IDs, service identity and outcome without logging secrets or sensitive payloads.
