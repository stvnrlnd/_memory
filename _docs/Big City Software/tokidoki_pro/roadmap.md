# tokidoki.pro — Roadmap & Feature Set

## The MVP Question

The risk with this product is building three things (project management + KPI tracking + meeting generation) before any of them are good enough to be useful. The MVP should answer one question: **can generated meeting agendas, built from real work data, make a team's meetings noticeably better?**

Everything in MVP exists to answer that question. Everything else is deferred.

---

## MVP — "Does this work?"

Goal: get in front of one real team (ABHP or otherwise) and have them say *"this made our meeting better."*

### Auth & Workspace
- Email/password auth
- Single workspace per account (no multi-org in MVP)
- Basic user invites (email invite, accept link)

### Projects
- Create/rename/archive projects
- Project description
- No teams concept yet — projects are the top-level org unit in MVP

### KPIs
- Create custom KPIs per project (name, unit, cadence: weekly/monthly)
- Manual entry per period (a simple form, logged with date)
- Sparkline or simple trend view per KPI (last N entries)
- This is the primary data input that feeds meeting generation

### Tasks
- Simple task list per project (title, status: open/in progress/done, optional assignee)
- No subtasks, no priorities, no sprints — just enough to surface blockers
- Tasks can be flagged as a blocker manually

### Meeting Generation
- Trigger a meeting for a project
- Generated agenda is rigid and fixed in MVP — no customization, no templates yet
- Agenda sections (always in this order):
  1. **KPI Review** — each KPI with latest value, delta from prior period, trend indicator
  2. **Blockers** — flagged tasks pulled automatically
  3. **Open Items** — manually added agenda items (free text)
  4. **Decisions** — empty section to capture during the meeting
- Agenda items within sections can be added/removed, but the section structure is locked
- Save the completed meeting (decisions + action items captured as free text)

### What MVP deliberately excludes
- Teams as a separate entity
- Async meeting mode
- Recurring meeting cadences
- Action items auto-converting to tasks
- Any KPI automation or integrations
- Roles/permissions beyond owner vs. invited member

---

## V1.0 — "Is this worth paying for?"

Goal: first paying customer. The product is coherent, not just a demo.

### Teams
- Introduce Teams as an explicit entity separate from Projects
- A team can own multiple projects
- Meeting generation can optionally span a team's projects (roll-up view)

### Meeting Cadence
- Set a recurring meeting cadence per project or team (weekly, bi-weekly, monthly)
- Reminders to enter KPIs before scheduled meeting
- Meeting history — past agendas preserved, searchable

### Action Items
- Capture action items during a meeting with assignee + due date
- Action items appear as tasks in the relevant project automatically
- Prior meeting's open action items surfaced in the next agenda

### KPI Dashboard
- Project-level dashboard showing all KPIs with trend charts over time
- Quick-entry view for logging multiple KPIs at once (reduces friction for weekly habit)

### User Roles
- Admin (full access, billing)
- Member (create/edit tasks and KPIs, run meetings)
- Viewer (read-only)

### Billing
- Flat monthly fee per workspace — unlimited users (Basecamp model)
- Free tier: 1 project, limited KPI history (structure TBD)
- Paid tier: unlimited projects, full history, team features
- Price point TBD — see `pricing.md`

---

## V1.x — Near-Term Additions

These are well-defined enough to plan for but not blocking a first customer.

- **Async meeting mode** — send the generated agenda for async review; comments/reactions per section; only unresolved items escalate to a sync call
- **Slack integration** — post meeting summaries to a channel, KPI entry reminders
- **KPI entry via Slack** — `/kpi [project] [metric] [value]` shortcut to reduce friction
- **Meeting templates** — save and reuse agenda structures across projects; foundation for a future template marketplace
- **Guest access** — share a read-only meeting agenda link externally

---

## Future / Backlog

Ideas worth keeping but not yet scoped:

- AI-generated insights from KPI trends ("revenue has declined 3 weeks in a row — flagging for agenda")
- Calendar integration (create calendar events from meeting cadence)
- KPI automation via webhooks or third-party integrations (Stripe, Google Analytics, etc.)
- Native mobile app or PWA
- Full async-first mode where sync meetings become the exception
- Public KPI dashboards (transparency mode for startups)
- **Template marketplace** — community-created meeting templates; potential acquisition and monetization channel

---

## Open Questions (blocking v1 scoping)

- [x] Pricing model — flat fee per workspace (Basecamp model); price point TBD
- [x] Tech stack decision
- [x] ABHP design partner evaluation
- [x] Meeting structure — rigid 4-section format for MVP; templates in V1.x; marketplace in future
