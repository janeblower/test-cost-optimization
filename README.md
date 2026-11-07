# Test Cost Optimization

An agent skill for reducing unnecessary test runs and keeping test output manageable across projects, languages, and stacks.

## Problem

As a project grows, an AI coding agent adds tests for new features and regressions. The resulting suite provides valuable coverage, but running it broadly and repeatedly for every change takes more time as the project expands.

Test output grows too. When an agent reads long logs, polls jobs frequently, or revisits the same results, it spends more tokens and context on verification. A task similar to one that was inexpensive earlier in the project can therefore become slower and more costly, even when the change itself is no more complex. Verbose output can also bury the failures that matter.

## Approach

Plan checks around the change, run focused tests first, and finish with the required broader checks. Rerun only what changes affect unless wider verification is warranted. Keep concise summaries and retain full logs for diagnosis, without hiding failures or weakening required checks.

The skill instructions are in [SKILL.md](SKILL.md).

## Installation

Install for your user with curl (overwrites an existing `SKILL.md`):

**Claude Code**

```sh
mkdir -p ~/.claude/skills/test-cost-optimization
curl -fL https://raw.githubusercontent.com/janeblower/test-cost-optimization/main/SKILL.md -o ~/.claude/skills/test-cost-optimization/SKILL.md
```

**Codex**

```sh
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills/test-cost-optimization"
curl -fL https://raw.githubusercontent.com/janeblower/test-cost-optimization/main/SKILL.md -o "${CODEX_HOME:-$HOME/.codex}/skills/test-cost-optimization/SKILL.md"
```

Restart the agent to discover the skill.
