---
name: Kafka messaging standards
description: Kafka producer, consumer, event contracts, delivery semantics and reliability.
applyTo: "**/*Producer*.java,**/*Consumer*.java,**/*Listener*.java,**/*Event*.java,**/*Kafka*.java,**/kafka/**"
---
# Kafka standards
- Define event name, schema, ownership, key, ordering requirement and compatibility policy before coding.
- Use stable event envelopes with event ID, event type, schema version, occurrence time, producer and correlation/trace identifiers where appropriate.
- Choose partition keys based on required ordering; Kafka ordering is per partition, not global.
- Assume consumers can receive duplicates. Make business effects idempotent using event IDs or domain idempotency keys with durable deduplication.
- Configure producer acknowledgements, retries, idempotence and delivery timeouts deliberately for the selected Kafka client version.
- Do not confuse Kafka producer idempotence with end-to-end exactly-once business processing.
- Commit offsets only after the intended processing outcome is durable; define retry and recovery behavior.
- Use bounded retries, backoff and a dead-letter strategy with operational ownership and replay procedure.
- Avoid infinite retry loops and poison-message blocking.
- Use the transactional outbox when a database update and event publication must be coordinated reliably.
- Use inbox/deduplication patterns when consumer side effects must be protected from redelivery.
- Avoid large messages; store large payloads in object storage and publish references when appropriate.
- Secure Kafka with TLS and authentication/authorization appropriate to the environment.
- Add tests for duplicate, out-of-order, poison, retry, replay and consumer restart scenarios.
