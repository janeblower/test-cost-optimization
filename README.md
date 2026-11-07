# Test Cost Optimization

An agent skill for reducing unnecessary test runs and keeping test output manageable across projects, languages, and stacks.

## Problem

Repeated broad test runs waste time, while verbose logs consume agent context and can bury the failures that matter.

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
