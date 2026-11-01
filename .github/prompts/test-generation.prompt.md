# Generate meaningful tests

Target class/feature: ${input:target:Class or feature to test}

Inspect production code, existing tests and build dependencies first. Use the project's actual test framework and conventions.

Create tests for:
- Expected behavior and business invariants.
- Null, empty, malformed and boundary inputs.
- Validation and exception mapping.
- Authorization and tenant/object ownership where applicable.
- Database constraints and transaction behavior.
- Duplicate messages/requests and concurrency where relevant.
- External dependency timeout, failure and retry behavior.

Prefer deterministic tests. Do not mock the class under test. Use Testcontainers only if supported and justified. Do not change production behavior merely to satisfy a test. Report exact test commands and results.
