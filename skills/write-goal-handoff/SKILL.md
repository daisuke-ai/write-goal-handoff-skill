---
name: write-goal-handoff
description: Write execution-ready Markdown handoffs for Codex `/goal` runs, including a short goal launcher prompt, authority stack, ordered phases, hard rules, verification gates, and final report requirements. Use when the user asks for a handoff, next-session plan, goal file, `/goal` prompt, agent execution contract, implementation handoff, or wants a Markdown file another AI agent can execute without re-planning.
---

# Write Goal Handoff

## Overview

Create a handoff document that a fresh AI agent can execute through `/goal` without guessing architecture, scope, order, or completion criteria. Keep the `/goal` text short and put the detailed contract in Markdown.

## Workflow

1. Inspect the repo or source artifacts before writing. Read project instructions, existing handoff docs, relevant specs, current diffs/status, and named reference implementations.
2. Separate the short `/goal` launcher from the full handoff. The launcher should fit comfortably under 3500 characters and point to the Markdown file as the source of truth.
3. Write the handoff as an execution contract, not a brainstorming plan. Include objective, authority, exact scope, non-goals, phase order, hard rules, verification gates, completion criteria, and report format.
4. Make every phase independently checkable. Each phase needs deliverables, expected files or modules, required tests, grep/file-existence checks when useful, and pass/fail criteria.
5. Save the handoff to a Markdown file. Use an existing project handoff location if one exists; otherwise prefer `docs/handoffs/YYYY-MM-DD-<slug>.md` for repo work or `mktemp -t goal-handoff-XXXXXX.md` for temporary cross-project handoffs.
6. Final response should include the handoff path and the exact short `/goal` launcher to paste.

## Goal Launcher Rules

Write a launcher block that names the outcome, references the handoff path or attachment, and states that completion requires the handoff's verification gates. Do not duplicate the whole handoff in `/goal`.

Use this shape:

```text
/goal Execute <handoff title> from <handoff path>.

Treat that handoff as the source of truth. Complete phases in order, obey all hard rules, run every verification gate, update docs where required, and return the final implementation report requested in the handoff. The goal is complete only when all listed completion criteria pass or an explicit blocker is reported with evidence.
```

Only call Codex goal-setting tools if the user explicitly asks to create or update the active goal. Otherwise, produce the launcher text for the user to run.

## Handoff Content Requirements

Include these sections unless the task makes one irrelevant:

- `Goal Launcher`: paste-ready `/goal` command.
- `Execution Contract`: objective, source-of-truth hierarchy, branch/cwd, and completion definition.
- `Scope`: in-scope, out-of-scope, and assumptions that must be verified.
- `Architecture References`: exact files, modules, tests, docs, commits, or prior implementations to copy.
- `Hard Rules`: negative constraints, anti-patterns, coding rules, data rules, and stop conditions.
- `Execution Order`: numbered phases that are safe to run one at a time.
- `Per-Phase Checklist`: deliverables, TDD expectations, file targets, verification commands, and docs updates.
- `Verification Matrix`: commands with cwd, expected pass condition, and what to do on failure.
- `Final Report Format`: files changed, tests added, commands run, pass/fail results, deviations, blockers, and follow-up cleanup.

See [references/handoff-template.md](references/handoff-template.md) for a copyable structure.

## Quality Bar

- Prefer exact file paths, commands, and existing pattern references over conceptual instructions.
- Preserve user-provided wording for hard rules and source-of-truth decisions.
- Mark unknowns as assumptions to verify; do not invent repo state, endpoints, schemas, tests, or metrics.
- Make blockers explicit: what failed, exact evidence needed, and whether to stop or continue with another phase.
- Do not bury verification in prose. Put it in a checklist or table the executing agent can mechanically follow.
- Keep handoffs implementation-ready but not over-prescriptive about tiny code edits the executor should discover from the repo.

## Common Mistakes To Avoid

- Do not make `/goal` carry the whole plan; long goal text is brittle and hard to inspect.
- Do not write "run tests" without naming the actual commands and the expected pass signal.
- Do not say "follow existing patterns" without naming the exact files or functions.
- Do not merge multiple phases into one vague task when the executor needs gates between them.
- Do not declare success criteria that cannot be verified from the local repo, logs, tests, or user-provided artifacts.
