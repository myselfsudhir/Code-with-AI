# Evidence-led debugging

Problem: ${input:problem:Describe the observed failure}
Expected behavior: ${input:expected:What should happen}
Observed error/logs: ${input:evidence:Paste exact error, stack trace or logs}

Do not guess the root cause immediately.

1. Inspect relevant code/configuration and exact dependency versions.
2. Trace the execution path and identify where observed behavior diverges from expected behavior.
3. List hypotheses ranked by evidence, not intuition.
4. Propose the smallest diagnostic step for each leading hypothesis.
5. Do not claim a root cause until evidence supports it.
6. Implement a fix only after explaining the root cause and receiving approval if the change is broad or risky.
7. Add a regression test and report actual verification.

Never fabricate log lines, command output or runtime state.
