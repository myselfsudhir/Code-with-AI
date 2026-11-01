# Evidence and hallucination audit

Audit the proposed answer or code change: ${input:artifact:Describe or reference the answer/change}

For every material claim, API, class, method, annotation, dependency, configuration key, endpoint, schema field, event field, command and test result:
1. Find evidence in the repository or authoritative version-matched documentation.
2. Mark it Verified, Assumption, Unknown or Incorrect.
3. Remove or correct unsupported claims.
4. Identify version mismatches and incompatible recommendations.
5. Check that test/build/deployment claims are backed by actual command output.

Do not create fake citations or pretend to have run commands. Return a table of claim, status, evidence and correction. Explicitly state what could not be verified.
