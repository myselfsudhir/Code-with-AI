# Design a service-owned data model

Service and use cases: ${input:service:Service and its responsibilities}
Known queries/workload: ${input:queries:Read/write patterns and scale if known}
Consistency requirements: ${input:consistency:Required consistency and transaction boundaries}

Inspect existing schemas and migrations. Compare PostgreSQL, MySQL and MongoDB only against the stated access patterns. Consider Redis separately for cache/ephemeral coordination.

Provide entities/documents, relationships, constraints, indexes, transaction boundaries, migration and rollback strategy, data ownership, retention, backup/restore and security. Do not invent workload numbers. Label unknowns and ask for them. Do not execute SQL or modify migrations unless explicitly requested.
