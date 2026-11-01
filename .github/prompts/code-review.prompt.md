# Production-grade code review

Review the current diff and relevant surrounding code. Do not edit files.

Check correctness, data integrity, SOLID/design quality, security, authorization, input validation, transaction boundaries, SQL/JPA behavior, Kafka duplicates/order/retries, distributed timeouts, idempotency, observability, performance and test coverage.

For each finding provide:
- Severity: Critical / High / Medium / Low.
- Evidence: file, symbol and line where available.
- Concrete failure or exploit scenario.
- Why existing tests may miss it.
- Specific remediation.
- Suggested regression test.

Do not invent findings. Distinguish confirmed defects from risks requiring more information. End with review scope and limitations.
