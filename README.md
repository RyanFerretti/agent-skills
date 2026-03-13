# agent-skills

A collection of custom skills for Claude Code and other AI coding agents.

## Skills

- **get-date** — Returns the current date and time
- **codex-review** — Iterative code review loop between Claude and OpenAI Codex CLI

## Usage

Create a new skill:

```bash
npm skill init
```

Install a skill:

```bash
npx skills add [path to skill dir]
```

**Updating skills:** `npx skills update` doesn't track locally installed skills, so after editing a skill you need to manually copy the updated file: `cp <skill-dir>/SKILL.md ~/.agents/skills/<skill-name>/SKILL.md`. See [vercel-labs/skills#337](https://github.com/vercel-labs/skills/issues/337) for details.
