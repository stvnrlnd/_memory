# tokidoki.pro — Tech Stack

## Core

- **Laravel** — application framework
- **Statamic** — marketing/content pages
- **Filament** — app UI (dashboard, KPI entry, task management, meeting views)

## Rationale

Laravel is Steven's primary framework across all Big City Software projects, making it the natural default. Statamic handles marketing pages cleanly without requiring a separate CMS. Filament provides a polished, rapid-development UI layer for the data-dense parts of the app (KPI tables, meeting views, project dashboards) without building a custom frontend from scratch.

## Notes

- Filament's resource/panel model maps well to tokidoki.pro's core entities (Projects, KPIs, Tasks, Meetings).
- Real-time features (if needed for async meeting mode in V1.x) can be handled via Laravel Reverb or Pusher.
- Authentication via Laravel's built-in auth; multi-tenancy likely via a package like Tenancy for Laravel or a simple team-scoped approach depending on the pricing/isolation model decided.
