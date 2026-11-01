---
name: Java 21 standards
description: Java language, API design, collections, concurrency and maintainability rules.
applyTo: "**/*.java"
---
# Java 21 standards
- Target the Java version declared in the build; project baseline is Java 21 unless the build proves otherwise.
- Prefer readable, idiomatic Java over clever code.
- Use records for immutable DTOs, events and value objects when their semantics fit. Do not use records for JPA entities or mutable lifecycle-managed objects.
- Use sealed types, pattern matching, switch expressions and text blocks only when they improve clarity and are supported by the configured compiler.
- Use `var` only when the initializer makes the type obvious.
- Prefer immutable values and defensive copies at boundaries.
- Use `equals`/`hashCode` consistently for value types; do not use mutable fields as hash keys.
- Use try-with-resources for closeable resources.
- Handle interruption correctly; do not swallow `InterruptedException`.
- Avoid shared mutable state. Document concurrency assumptions.
- Use `Optional` primarily for return values, not fields, parameters or collections.
- Avoid raw types, unchecked casts and broad `catch (Exception)` unless a boundary layer has a documented reason.
- Validate inputs at system boundaries.
- Do not introduce Lombok if the project does not already use it; records and IDE generation may be sufficient.
