---
name: Persistence and database standards
description: SQL, JPA, schema migrations, transactions, MongoDB and Redis guidance.
applyTo: "**/*Repository.java,**/*Entity.java,**/*Document.java,**/*Mapper.java,**/db/**,**/migration/**,**/*Migration*.java"
---
# Database standards
- Treat each service as owner of its data. Avoid shared writable schemas between services.
- Inspect existing schema, migrations, indexes and query patterns before proposing changes.
- Use Flyway or Liquibase only if already selected or approved; do not introduce a second migration framework.
- Never edit an already-applied production migration; create a forward-only migration.
- Use explicit constraints, indexes and appropriate data types; justify indexes against query patterns.
- Avoid N+1 queries; verify fetch plans and generated SQL for performance-sensitive paths.
- Use pagination for unbounded result sets.
- Use optimistic or pessimistic locking only where the concurrency model requires it.
- Keep transaction boundaries local to one service/database.
- Use parameterized queries; never concatenate untrusted input into SQL.
- Do not assume MySQL and PostgreSQL have identical SQL, locking, JSON, sequence or migration behavior.
- Select PostgreSQL or MySQL based on workload and operational requirements; do not configure both in one service without a clear need.
- Use MongoDB only when document-shaped aggregates and access patterns justify it; model indexes and consistency deliberately.
- Use Redis with TTL, bounded memory, eviction strategy, key naming, serialization compatibility and explicit cache invalidation.
- A cache miss or Redis outage must have a documented fallback. Do not treat cache as durable truth by accident.
- Never store credentials or sensitive values in plain text.
