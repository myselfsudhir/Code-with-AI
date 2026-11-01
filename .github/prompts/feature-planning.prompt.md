# Plan a production-grade feature

Feature: ${input:feature:Describe the feature}
Business rules: ${input:rules:List known rules}
Constraints: ${input:constraints:List constraints}

Do not edit code yet.

Inspect the repository and produce:
- User/business flow and edge cases.
- API contract and validation.
- Domain model and service ownership.
- Database changes and migration plan.
- Kafka events and delivery/idempotency requirements, if relevant.
- Authentication and authorization requirements.
- Failure modes, timeouts, retries and consistency behavior.
- Observability requirements.
- Test strategy.
- Exact files/modules likely to change.
- Open questions and assumptions.

Do not invent requirements. Ask before making consequential assumptions.
