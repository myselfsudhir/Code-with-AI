---
name: Distributed systems reliability
description: Resilience, consistency, idempotency, timeouts, tracing and service boundaries.
applyTo: "**/src/main/**/*.java,**/src/main/resources/**,**/docker-compose*.yml,**/k8s/**,**/helm/**"
---
# Distributed systems standards
- Design around partial failure, network partitions, latency, retries and duplicate requests.
- Set explicit connection, response and end-to-end deadlines for remote calls.
- Retry only transient failures; use bounded attempts, exponential backoff and jitter. Avoid retry amplification.
- Use circuit breakers and bulkheads where justified by dependency behavior and traffic.
- Propagate trace context and correlation identifiers across HTTP and messaging boundaries.
- Make write APIs idempotent where clients or infrastructure may retry. Define key scope, persistence, expiry and response replay semantics.
- Do not claim distributed atomicity from local `@Transactional`.
- Use saga orchestration/choreography for multi-service business workflows when appropriate; define compensations and terminal failure handling.
- Use transactional outbox/inbox patterns when reliable state/event coordination is required.
- Define consistency expectations explicitly: strong/local, eventual, read-your-writes or other.
- Avoid synchronous call chains that create cascading latency and availability coupling.
- Define graceful degradation and dependency outage behavior.
- Never expose internal service addresses or sensitive topology in public errors.
