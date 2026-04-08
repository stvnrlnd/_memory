# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## About This Workspace

This is the admin layer for Steven Roland's work as CEO and sole developer of Segment Holdings. It serves as a shared knowledge base between Steven and Claude across multiple businesses and projects.

- **`_docs/`** — High-level thinking, project overviews, and business plans. Organized into group folders by entity or client, with a subfolder per project. Start here for context on any project.
- **`_sites/`** — Web project code. Each site is tracked in its own git repository and has its own `CLAUDE.md` with project-specific technical guidance.

The root directory is an Obsidian vault (`.obsidian/`), with `_docs/` as its organized content.

## How We Work Together

Steven is both the CEO and the sole developer across all projects. This workspace exists so that Claude has the context needed to assist across those projects effectively — from high-level strategy to implementation.

When starting work on a project:
- Look in `_docs/[Group]/[project]/` for product context, business goals, and decisions
- Look in `_sites/[project]/CLAUDE.md` for technical guidance

When creating new project documentation, place it in the appropriate `_docs/[Group]/[project]/` folder.

When starting or continuing work on any project, check whether a `changelog.md` exists in its `_docs/` folder. If it doesn't, create one. As work is done — whether code, documentation, or decisions — add a dated entry to the changelog. Admin and documentation work counts and should be recorded.

## Dart (Project Management)

Dart is the project management tool for Segment Holdings. Access it via MCP tools (`mcp__Dart__*`).

### Spaces & Dartboards

Tasks are organized into team spaces, each with a dartboard:

| Space | Dartboard | Purpose |
|---|---|---|
| Leadership | Leadership/Tasks | High-level ideas and directional tasks — Steven's starting point |
| Engineering | Engineering/Active, /Next, /Sprint 1, /Sprint 2, /Backlog | Dev work |
| Product | Product/Tasks | Product decisions and specs |
| Design | Design/Tasks | Design work |
| Sales | Sales/Tasks | Sales activity |

### Workflow

Steven's typical flow:
1. A new idea or initiative starts as a task in **Leadership/Tasks** — these are often directional/exploratory and may not yet have a project tag.
2. Leadership tasks may spin off subtasks assigned to Engineering, Product, Design, or Sales dartboards.
3. Tasks in team dartboards (non-Leadership) should have a **project** tag applied to link them to a specific project.

### Custom Properties

- **`project`** (multiselect) — Links a task to one or more projects. Current values include: `sendfeed.to`, `segment.holdings`, `firstcitysoftware.com`, `homestead.plus`, `openfaith.world`, `stevenroland.com`, `allgood-roland.org`, `montanna.pro`, `theirvoice.blog`, `theoandchar.com`, and others. Apply this to all non-Leadership tasks.
- **`importance`** (select) — `Critical`, `Priority`, `Pickup`, `Optional`.

### Task Types & Statuses

- **Types:** Task, Bug, Feature, Experimental, Maintenance, Security
- **Statuses:** Ready, In Progress, On Hold, Done, Left

### Assignees

- Steven Roland (`steven@segment.team`) — CEO and sole developer; default assignee for most tasks
- Montanna Allgood (`montanna@segment.team`)
- Dart AI
