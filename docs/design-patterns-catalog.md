# Design Patterns Catalog

Use this as a reference, not a checklist. A pattern is justified only when it reduces real complexity or supports a required quality attribute. Prefer simple code when it is clearer.

## 1. GoF creational patterns

| Pattern | Intent | Java / Spring example | Use when |
|---|---|---|---|
| Abstract Factory | Create families of related objects | Provider-specific client factories | Families must vary together |
| Builder | Construct complex objects step by step | Immutable configuration/complex DTO builder | Many optional construction parameters |
| Factory Method | Delegate object creation to subclasses/implementations | Payment method factory | Creation varies by type |
| Prototype | Create objects by copying a prototype | Template-based configuration objects | Copying is safer/cheaper than reconstructing |
| Singleton | One shared instance | Spring singleton-scoped bean | Stateless shared service; Spring already manages lifecycle |

## 2. GoF structural patterns

| Pattern | Intent | Java / Spring example | Use when |
|---|---|---|---|
| Adapter | Convert one interface to another | Third-party payment provider adapter | Integrating external systems |
| Bridge | Separate abstraction from implementation | Multiple notification channels and delivery providers | Two dimensions vary independently |
| Composite | Treat individual and grouped objects uniformly | Nested product/category structures | Tree structures |
| Decorator | Add behavior without changing original type | Metrics/retry wrapper around a client | Composable cross-cutting behavior |
| Facade | Simplify a complex subsystem | Application service coordinating domain operations | Consumers need a simpler API |
| Flyweight | Share intrinsic state to reduce memory | Shared immutable metadata | Many similar objects create memory pressure |
| Proxy | Control access to another object | Spring AOP, transactional/security proxies | Lazy access, access control or remote boundary |

## 3. GoF behavioral patterns

| Pattern | Intent | Java / Spring example | Use when |
|---|---|---|---|
| Chain of Responsibility | Pass request through handlers | Servlet/Spring Security filter chain | Ordered handlers may accept/stop processing |
| Command | Encapsulate request as an object | Job/command handlers | Queueing, audit, retry or undo is needed |
| Interpreter | Evaluate a small grammar | Rules/filter expression engine | A domain-specific language is justified |
| Iterator | Traverse a collection without exposing internals | Java Iterator/Stream | Collection traversal abstraction |
| Mediator | Centralize interactions between peers | Workflow coordinator | Peer-to-peer dependencies are becoming tangled |
| Memento | Capture and restore state | Draft/version snapshots | State rollback/history is required |
| Observer | Notify dependents of state changes | Spring events, domain events | Publisher should not know subscribers |
| State | Change behavior based on internal state | Order/payment state machine | Many state-dependent conditionals |
| Strategy | Encapsulate interchangeable algorithms | Pricing/tax/payment strategies | Algorithm varies by policy or context |
| Template Method | Define algorithm skeleton with variable steps | Abstract batch processing | Stable workflow with controlled extension points |
| Visitor | Add operations across object structures | AST operations | Object structure is stable, operations vary |

## 4. Enterprise application patterns

- Repository: domain-oriented persistence abstraction.
- Unit of Work: track changes within a transaction; ORM frameworks often provide this.
- Data Mapper: map persistence structures to domain objects.
- Data Transfer Object (DTO): carry data across process/API boundaries.
- Service Layer: define application operations and transaction boundaries.
- Domain Model: encapsulate business behavior and invariants.
- Specification: encapsulate reusable business predicates.
- Identity Map: ensure one in-memory object per identity in a unit of work.
- Lazy Load: defer loading until needed; watch for N+1 queries.
- CQRS: separate read and write models when their needs materially differ.
- Hexagonal / Ports and Adapters: isolate domain/application logic from infrastructure.
- Dependency Injection: supply dependencies externally.

## 5. Distributed systems and messaging patterns

- API Gateway: single edge entry point for routing and cross-cutting concerns.
- Backend for Frontend (BFF): client-specific API composition.
- Circuit Breaker: stop repeated calls to a failing dependency.
- Retry with Backoff and Jitter: retry transient faults without synchronized retry storms.
- Bulkhead: isolate resource pools/failure domains.
- Timeout / Deadline: bound waiting across calls.
- Rate Limiter: control request rate.
- Saga: coordinate multi-service business transactions with compensations.
- Transactional Outbox: atomically persist business state and an event record locally.
- Transactional Inbox / Idempotent Consumer: deduplicate message processing.
- Event Sourcing: persist state changes as an event log; use only when audit/history/reconstruction justify complexity.
- CQRS: separate command and query models.
- Strangler Fig: incrementally replace a legacy system.
- Anti-Corruption Layer: translate between external/legacy models and the domain.
- Service Discovery: locate dynamic service instances.
- Leader Election: coordinate one active worker where required.
- Sharding: partition data across nodes.
- Read Replica: scale reads with replication-lag awareness.
- Cache-Aside: application manages cache reads and invalidation.
- Write-Through / Write-Behind: cache write strategies with explicit durability trade-offs.
- Dead Letter Queue (DLQ): isolate messages that cannot be processed.
- Competing Consumers: parallelize message processing.
- Consumer Retry: retry failed messages with bounded policy.
- Event-Carried State Transfer: publish enough event data to maintain a local read model.

## 6. Pattern selection checklist

Before adopting a pattern, answer:
1. What concrete problem exists today?
2. Which requirement or quality attribute does it address?
3. What is the simplest alternative?
4. What complexity and operational cost does it add?
5. How will it be tested and observed?
6. Is it consistent with current service boundaries?
7. Is there a failure mode or consistency trade-off?

Do not apply Singleton manually to Spring beans, use Event Sourcing by default, or add CQRS/Saga/DDD layers merely to appear enterprise-grade.
