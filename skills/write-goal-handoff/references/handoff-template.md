# Goal Handoff Template

Use this as a structure, not as fixed prose. Delete sections that are truly irrelevant.

````markdown
# <Handoff Title>

## Goal Launcher

```text
/goal Execute <handoff title> from <absolute-or-repo-relative-path>.

Treat this handoff as the source of truth. Complete phases in order, obey all hard rules, run every verification gate, update docs where required, and return the final implementation report requested below. The goal is complete only when all completion criteria pass or an explicit blocker is reported with evidence.
```

## Execution Contract

- Cwd:
- Branch:
- Source of truth:
- Objective:
- Completion definition:

## Scope

In scope:
- 

Out of scope:
- 

Assumptions to verify before editing:
- 

## Authority

1. User-provided handoff or attached document:
2. Project instructions:
3. Existing implementation patterns:
4. Current tests/build output:

## Architecture References

- Pattern reference:
- Schema or type reference:
- Runner/API/UI reference:
- Existing tests:
- Docs to update:

## Hard Rules

- 

## Execution Order

1. <Phase 1>
2. <Phase 2>
3. <Phase 3>

## Per-Phase Checklist

### Phase 1: <Name>

Deliverables:
- 

TDD gate:
- [ ] Write or update failing tests first.
- [ ] Confirm the expected failure before implementation when practical.

Implementation:
- [ ] 

Verification:
- [ ] `<command>` from `<cwd>` must pass.
- [ ] `<grep/check>` must prove `<condition>`.

Move-on rule:
- Do not start the next phase until every required check above passes or the blocker is reported.

## Verification Matrix

| Gate | Cwd | Command | Expected result |
| --- | --- | --- | --- |
| Types/build | `<cwd>` | `<command>` | Passes with zero new errors |
| Tests | `<cwd>` | `<command>` | Relevant suite passes |
| Search check | `<cwd>` | `<command>` | Confirms forbidden pattern is absent or required pattern exists |

## Failure Protocol

- If a command fails, capture the command, exit signal, and shortest useful error excerpt.
- If the handoff conflicts with current repo truth, stop and report the conflict before redesigning.
- If an external dependency is unavailable, mark the exact verification as blocked and continue only when the handoff allows it.

## Final Implementation Report

Return:
- Files changed
- Tests added or updated
- Commands run
- Pass/fail results
- Intentional deviations from this handoff
- Blockers or follow-up cleanup items
````
