# Database Selection Guide

## PostgreSQL
Good default for services needing relational integrity, expressive SQL, transactions, JSONB where useful, and strong indexing/query capabilities.

## MySQL
Good relational option where the operational ecosystem, team expertise, compatibility or existing platform favors it. Validate SQL dialect, locking and migration behavior separately from PostgreSQL.

## MongoDB
Use for document-oriented aggregates, flexible nested documents and access patterns that read/write documents as a unit. Do not choose it solely because schemas can vary. Model indexes, document growth, consistency and multi-document transaction requirements.

## Redis
Use for cache-aside, rate limiting, ephemeral coordination, short-lived tokens/state or carefully designed distributed primitives. Define TTL, eviction, persistence, failover, cache invalidation and outage behavior. Do not silently treat it as the system of record.

## Decision checklist
- What are the dominant read/write access patterns?
- What consistency and transaction guarantees are required?
- What are the data relationships and constraints?
- How will indexes and query plans be validated?
- What are backup, restore, retention and migration requirements?
- What is the operational expertise/cost?
- What is the failure behavior if this datastore is unavailable?

Do not deploy every database in every service. Choose the smallest set that meets the workload.
