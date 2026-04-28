# CLAUDE.md

This file provides guidance to Claude Code when working in this repository.

## About This Workspace

This is Steven Roland's personal Obsidian vault — a shared knowledge base and workspace between Steven and Claude. It covers multiple businesses and projects under [[20_areas/segment-holdings|Segment Holdings LLC]].

Steven is both the CEO and sole developer across all projects. He is a PHP/Laravel developer based in Pensacola, FL. He also works a day job at America's Best House Plans (ABHP).

## Vault Structure

```
00_inbox/       — Fleeting ideas and captures. Add ideas here during brainstorming.
10_projects/    — One subfolder per project. Start here for any project context.
20_areas/       — Ongoing responsibilities: groups, subsidiaries, company overview.
30_resources/   — Reference material shared across projects.
40_archives/    — Cold storage: completed/abandoned work; includes daily notes and meetings.
  daily/        — Daily notes (YYYY-MM-DD.md).
  meetings/     — Meeting notes.
90_system/      — Claude's context and system files. See context.md and vault-guide.md.
```

For full vault conventions (frontmatter format, linking style, Dart structure), see [[90_system/vault-guide]].

For background on Steven, the company, and active project status, see [[90_system/context]].

## Code Location

Project code lives outside this vault: `~/Work/_code/[project]/`. Each has its own git repo and `CLAUDE.md` with technical guidance.

## How We Work Together

### Starting work on a project

1. Read `10_projects/[project]/overview.md` for product context, goals, and current status.
2. Check `~/Work/_code/[project]/CLAUDE.md` for technical guidance.
3. Check or create `10_projects/[project]/changelog.md` — log all work done (code, docs, decisions).

### Brainstorming and ideas

If an idea comes up during a brainstorm, create a note in `00_inbox/` immediately. Don't wait.

### Daily notes

Create a daily note at `40_archives/daily/YYYY-MM-DD.md` when starting a session if one doesn't exist. Log what was done at the end of the session. Use these to provide a morning brief when asked.

### Obsidian conventions

- Use YAML frontmatter on all notes (title, type, created at minimum).
- Use wiki links `[[filename]]` for internal links — not markdown relative links.
- **Always link** projects, areas, tasks, and any other referenceable notes when mentioning them in any vault file or daily note. This applies everywhere: briefs, logs, changelogs, meeting notes, inbox captures, and system files.
- Keep `type` consistent: `project`, `area`, `resource`, `system`, `daily`.

## Dart (Project Management)

Dart is the project management tool. Access via MCP tools (`mcp__Dart__*`). Full structure, dartboards, statuses, and custom properties are documented in [[90_system/vault-guide]].
