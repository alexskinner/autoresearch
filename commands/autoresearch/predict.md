---
name: autoresearch:predict
description: Multi-persona swarm prediction — pre-analyze code from multiple expert perspectives using file-based knowledge representation. Zero external dependencies.
argument-hint: "[goal/focus] [--scope <glob>] [--chain debug|security|fix|ship|scenario] [--depth shallow|standard|deep] [--personas N] [--rounds N] [--adversarial] [--budget <dollars>] [--fail-on <severity>]"
---

EXECUTE IMMEDIATELY — do not deliberate, do not ask clarifying questions before reading the protocol.

## Argument Parsing (do this FIRST)

Extract these from $ARGUMENTS — the user may provide extensive context alongside flags. Ignore prose and extract ONLY flags/config:

- `--scope <glob>` or `Scope:` — file globs to analyze
- `--chain <targets>` or `Chain:` — comma-separated: debug,security,fix,ship,scenario
- `--depth <level>` or `Depth:` — shallow (3 personas, 1 round), standard (5, 2), deep (8, 3)
- `--personas N` — number of personas (3-8)
- `--rounds N` — debate rounds (1-3)
- `--adversarial` — use red team personas
- `--budget <$>` — max cost per session
- `--fail-on <severity>` — CI/CD gate
- `--dry-run` — show what would happen without executing
- `Goal:` — text after "Goal:" keyword

All remaining text not matching flags is the goal/focus description.

## Execution

1. Read the predict workflow: `.claude/skills/autoresearch/references/predict-workflow.md`
2. If scope or goal is missing — use `AskUserQuestion` with batched questions per predict-workflow.md
3. Execute the 8-phase predict workflow
4. If `--chain` is set, hand off to each chained command sequentially

Stream all output live — never run in background.
