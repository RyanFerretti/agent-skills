# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Is

A collection of custom Claude Code agent skills (slash commands). Each skill lives in its own directory with a `SKILL.md` file that defines the skill's behavior, triggers, and instructions.

## Repo Structure

- Each top-level directory (e.g., `get-date/`, `codex-review/`) is a standalone skill
- Skills are defined entirely by a `SKILL.md` file using YAML frontmatter + markdown instructions
- `.agents/skills/` and `.claude/skills/` are empty skill registration directories

## Skill File Format

A `SKILL.md` has this structure:

```markdown
---
name: <skill-name>
description: <when/how to trigger this skill>
allowed-tools: <comma-separated list of tools the skill can use> (optional)
color: <terminal color> (optional)
---

# Skill Title

Instructions for Claude when this skill is invoked.
```

## Commands

- **Create a new skill**: `npm skill init`
- **Register a skill**: `npx skills add [path to skill dir]`

## After Editing a Skill

Edits in this repo don't propagate to the installed copies automatically (`npx skills update` doesn't track local skills). After committing changes to a skill, copy the updated file to the installed location:

```bash
cp <skill-dir>/SKILL.md ~/.agents/skills/<skill-name>/SKILL.md
```

For example: `cp codex-review/SKILL.md ~/.agents/skills/codex-review/SKILL.md`

`~/.claude/skills/<skill-name>` symlinks to `~/.agents/skills/<skill-name>`, so the copy is all that's needed.

## Current Skills

- **get-date**: Simple skill that runs `date` — good reference for minimal skill structure
- **codex-review**: Complex iterative review loop between Claude and OpenAI Codex CLI using `codex exec --json` with session resume via thread IDs
