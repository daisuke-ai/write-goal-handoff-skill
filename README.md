# Write Goal Handoff Skill

An agent skill for writing execution-ready Markdown handoffs that can be launched with a short Codex `/goal` prompt.

The skill helps an agent turn a plan, meeting note, issue, PR review, or migration brief into:

- a paste-ready `/goal` launcher
- a Markdown execution contract
- ordered phases with move-on gates
- hard rules and anti-patterns
- verification commands and pass/fail criteria
- final implementation report requirements

## Structure

```text
.
├── .claude-plugin/
│   └── marketplace.json
└── skills/
    └── write-goal-handoff/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            └── handoff-template.md
```

This follows the public Agent Skills convention: each skill is a self-contained folder with a required `SKILL.md` file and optional bundled resources.

## Install In Claude Code

Add the repository as a plugin marketplace:

```text
/plugin marketplace add daisuke-ai/write-goal-handoff-skill
```

Install the skill plugin:

```text
/plugin install write-goal-handoff@goal-handoff-skills
```

Then ask Claude Code to use the skill:

```text
Use the write-goal-handoff skill to turn this implementation plan into a Markdown handoff and a short /goal launcher.
```

## Install In Codex

Copy the skill folder into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/daisuke-ai/write-goal-handoff-skill.git /tmp/write-goal-handoff-skill
cp -R /tmp/write-goal-handoff-skill/skills/write-goal-handoff ~/.codex/skills/write-goal-handoff
```

Start a new Codex session so the skill index refreshes, then invoke it with:

```text
$write-goal-handoff turn this plan into a handoff file and /goal prompt
```

## Example Output Shape

```text
/goal Execute Phase 2 migration from docs/handoffs/phase-2-migration.md.

Treat that handoff as the source of truth. Complete phases in order, obey all hard rules, run every verification gate, and return the final implementation report requested in the handoff.
```

The full Markdown file carries the detailed objective, authority stack, scope, phase checklists, verification matrix, failure protocol, and final report format.

## License

MIT
