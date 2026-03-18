---
name: autoresearch:ship
description: Universal shipping workflow — ship code, content, marketing, sales, research, or anything through structured 8-phase workflow
argument-hint: "[--dry-run] [--auto] [--force] [--rollback] [--monitor N] [--type <type>] [--checklist-only]"
---

EXECUTE IMMEDIATELY — do not deliberate, do not ask clarifying questions before reading the protocol.

## Argument Parsing (do this FIRST)

Extract these from $ARGUMENTS — the user may provide extensive context alongside flags. Ignore prose and extract ONLY flags/config:

- `--dry-run` — validate everything but don't ship
- `--auto` — auto-approve if no errors
- `--force` — skip non-critical items (blockers enforced)
- `--rollback` — undo last ship action
- `--monitor N` — post-ship monitoring for N minutes
- `--type <type>` — override auto-detection (code-pr, code-release, deployment, content, etc.)
- `--checklist-only` — only generate checklist

All remaining text in $ARGUMENTS is additional context — use it to understand what's being shipped but do not treat it as flags.

## Execution

1. Read the ship workflow: `.claude/skills/autoresearch/references/ship-workflow.md`
2. If ship type is unclear — use `AskUserQuestion` with batched questions per ship-workflow.md
3. Execute the 8-phase ship workflow

Stream all output live — never run in background.
