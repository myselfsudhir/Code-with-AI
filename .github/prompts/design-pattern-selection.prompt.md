# Select a design pattern only when justified

Problem/context: ${input:problem:Describe the design problem}
Constraints: ${input:constraints:List constraints}

Read `docs/design-patterns-catalog.md` and inspect the existing code.

Compare:
- No pattern / straightforward implementation.
- Candidate pattern(s).
- Complexity introduced.
- SOLID principles affected.
- Testability and changeability.
- Runtime/performance implications.
- Fit with the current architecture.

Recommend a pattern only when it solves a demonstrated problem. Identify the pattern by its standard name and category, explain intent and show where it belongs. Do not force all GoF patterns into the codebase.
