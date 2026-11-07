---
name: test-cost-optimization
description: Reduce unnecessary test runs and agent context usage while preserving required verification. Use when planning, running, or improving verification for code changes, or when optimizing test reporting and logs.
---

# Cost-aware test verification

Reduce redundant work and output without weakening required checks. Choosing a better order can save execution time; concise reporting saves context, but does not make an already running test faster. Do not claim savings without measurements.

## Plan and run checks

- Identify affected components, risks, project requirements, and appropriate checks before running expensive suites. Follow explicit user and project requirements, including mandatory checks.
- Finish the core change and meaningful targeted regression coverage first. Diagnose and fix build or behavior failures with the narrowest relevant check. Then stabilize affected integration or end-to-end scenarios. For new or changed shared scenarios, compare expectations with an available reference; verify and document intentional differences separately.
- Once the change and targeted checks are stable, run the required final suite, static checks, and builds as appropriate. Reuse a successful result only while the relevant code, dependencies, configuration, environment, and scenario remain unchanged.
- After a fix, rerun affected checks. Repeat the broad suite when the impact is broad, dependencies change, requirements demand it, or correctness remains uncertain. Do not automatically repeat a full suite for every local failure.
- For an intermittent failure, preserve the first failure and rerun the test alone; if needed, run its suite serially to investigate interference. Report unresolved instability rather than treating a later pass as proof the failure is fixed.
- For documentation-only changes, check the diff, relevant links and syntax; run application tests only when required or relevant. Keep performance measurements isolated from concurrent builds and tests that could distort results.
- Poll long-running jobs at reasonable intervals rather than repeatedly reading unchanged output. Avoid restarting work merely to check progress.

## Keep output useful and bounded

Prefer an existing project runner or framework reporting facility. Capture complete stdout and stderr in a unique, non-overwriting log when appropriate, and return a concise summary: command outcome and exit status, duration, recognizable test counts including skipped or ignored tests, and log location. On failure, include failing case names and a bounded diagnostic excerpt; inspect the relevant part of the full log if the summary is insufficient. Never infer overall success from partial suite counts: use the command's actual exit status, and state when a summary cannot be parsed. Preserve launch errors, cancellation, and signal behavior. Do not stack redundant wrappers around an existing runner.

When creating or changing test reporting infrastructure, verify its handling of full logs, bounded diagnostics, skips, failed launches, failures after successful suites, and interruption where applicable. Adapt parsing to the actual framework; don't assume a particular output format.

## Write diagnostic tests

Keep passing tests quiet unless progress output is useful. Failures should identify the case, expected and actual behavior, relevant parameters, and any random seed. Describe large payloads with lengths, the mismatch location, short excerpts, or hashes instead of dumping everything. Enable per-iteration detail or full traces for diagnosis when needed. Mark skips explicitly with reasons, and never convert a failure into a successful exit. Improve noisy existing tests when working on them rather than rewriting a healthy suite solely for formatting.
