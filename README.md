# Test Cost Optimization

An agent skill for reducing unnecessary test runs and keeping test output manageable across projects, languages, and stacks.

## Problem

Repeated broad test runs waste time, while verbose logs consume agent context and can bury the failures that matter.

## Approach

Plan checks around the change, run focused tests first, and finish with the required broader checks. Rerun only what changes affect unless wider verification is warranted. Keep concise summaries and retain full logs for diagnosis, without hiding failures or weakening required checks.

The skill instructions are in [SKILL.md](SKILL.md).

## Installation

Install for your user with Git (the destination must not already exist):

**Claude Code**

```sh
mkdir -p ~/.claude/skills
git clone https://github.com/janeblower/test-cost-optimization.git ~/.claude/skills/test-cost-optimization
```

**Codex**

```sh
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone https://github.com/janeblower/test-cost-optimization.git "${CODEX_HOME:-$HOME/.codex}/skills/test-cost-optimization"
```

Restart the agent to discover the skill.
