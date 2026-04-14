---
title: System Context
type: system
tags:
  - system
  - context
created: 2026-04-13
---

# System Context

This file captures standing context that Claude should have in mind when working in this vault. It supplements CLAUDE.md with personal and business background.

## Steven Roland

- **Location:** Pensacola, FL
- **Role:** CEO and sole developer, Segment Holdings LLC
- **Stack:** PHP / Laravel / Statamic / Filament / Alpine.js / Tailwind / Vite
- **Day job:** Developer at America's Best House Plans (ABHP / houseplans.net), under the Director of Engineering
- **Contact:** `steven@segment.team`

## Montanna Allgood

- Steven's wife, partner, and collaborator. `montanna@segment.team`. The [[20_areas/allgood-roland|Allgood Roland]] group represents projects built with or for her.
- Has two children from a previous marriage: Theodore and Charlotte. nobullies.club and theoandchar.com are for them.
- Her projects (theirvoice.blog, montanna.me/pro/shop, allgood-roland.org, etc.) are solely hers — Steven builds and maintains them but they belong to her.

## Kelley Roland (group)

- "Kelley Roland" is a reference name for a project group, not a person. It uses Steven's mother's maiden name (her name is Julie Roland). The group covers projects shared with his mother or his brother.

## Segment Holdings LLC

- Florida LLC. Holding company structure intended, no subsidiaries incorporated yet.
- Self-funded. No external investors. No revenue yet.
- All projects operate under the LLC directly for now.

## How to Find Things

| What | Where |
|---|---|
| Project docs | `10_projects/[project].md` (main note) + `10_projects/[project]/` (supporting docs) |
| Area context | `20_areas/[area].md` |
| Shared references | `30_resources/` |
| Inbox (new ideas) | `00_inbox/` |
| Daily notes | `40_archives/daily/YYYY-MM-DD.md` |
| Meeting notes | `40_archives/meetings/` |
| Code | `~/Work/_code/[project]/` |
| This system | `90_system/` |

## Business Strategy

Steven's overall arc:
1. **Now** — freelance web dev + consulting under the Steven Roland brand to generate revenue
2. **Migration** — as Big City Software gains traction, migrate clients there; Steven Roland brand becomes a feeder
3. **Exit** — stop taking clients entirely; focus exclusively on Big City Software's SaaS products
4. **End goal** — pure software product company; no client dependency

Client work is a deliberate, time-limited bridge — not the destination.

## Active Projects (as of 2026-04-13)

### In Production

| Project | Notes | Group |
|---|---|---|
| [[10_projects/segment.holdings\|segment.holdings]] | Company site | Segment Holdings |
| [[10_projects/stevenroland.com\|stevenroland.com]] | Personal site / freelance / blog | Steven Roland |
| [[10_projects/theirvoice.blog\|theirvoice.blog]] | Montanna's anonymous blog | Allgood Roland |
| [[10_projects/allgood-roland.org\|allgood-roland.org]] | Family/org site | Allgood Roland |
| [[10_projects/firstcitysoftware.com\|firstcitysoftware.com]] | Relaunch planned | Big City Software |
| [[10_projects/flwr.page\|flwr.page]] | Link shortener utility | Segment Holdings |
| [[10_projects/openfaith.world\|openfaith.world]] | Faith project | Allgood Roland |

### In Development

| Project | Status | Group |
|---|---|---|
| [[10_projects/homestead.plus\|homestead.plus]] | In development | Kelley Roland |
| [[10_projects/sendfeed.to\|sendfeed.to]] | In development | Big City Software |
| [[10_projects/nobullies.club\|nobullies.club]] | In development | Allgood Roland |
| [[10_projects/hirethedude.com\|hirethedude.com]] | Pre-development | Big City Software |
| [[10_projects/tokidoki.pro\|tokidoki.pro]] | Ideation | Big City Software |

## Inbox

Random ideas and fleeting notes land in `00_inbox/`. When a brainstorm produces an actionable idea, Claude should create a note there immediately.

## Skills

- `/brief` — morning brief command. Reads active project context, delivers a brief in chat, writes a summary to the `## Brief` section of today's daily note. Defined at `.claude/commands/brief.md`.

## Obsidian Setup

- **Community plugins:** none installed
- **Template syntax:** core Templates plugin only — use `{{date:FORMAT}}`, not Templater syntax
- **Daily notes plugin:** configured — folder `40_archives/daily`, template `30_resources/templates/daily-note`
- **Templates plugin folder:** `30_resources/templates`
