# tokidoki.pro — Pricing

## Model

Tiered flat fee per workspace — no per-seat pricing. Each tier is a fixed monthly price regardless of how many users are in the workspace. Inspired by Basecamp's philosophy: pay for the tool, not per person.

Per-seat pricing is explicitly ruled out.

## Tiers

### Free — Individual
- 1 user
- 1 project
- Limited KPI history (e.g. last 30 days)
- Full meeting generation (so the core value is evaluable)
- No team features

### Team — $99/month ($79/month billed annually)
- Up to ~10–15 users
- Unlimited projects
- Full KPI history
- Meeting cadences and history
- Action items → tasks
- All V1.0 features

### Business — $199/month ($159/month billed annually)
- Unlimited users
- Everything in Team
- Priority support
- Future: advanced analytics, API access, SSO

## Open Questions

- **User cap on Team tier** — "small team" needs a defined ceiling. 10 users? 15? This also determines when someone needs to upgrade to Business.
- **Trial** — A time-limited trial of a paid tier (14–30 days) alongside the free individual plan may be more effective than relying on the free tier alone, since the meeting value compounds over time and is hard to see with limited data.

## Architecture Implications

Flat fee per tier means feature gating is at the workspace level — no per-seat counting or user-level entitlements. Multi-tenancy scoped to workspaces, with tier-level feature flags. Simpler than per-seat but user caps on the Team tier require basic seat tracking.

## Notes

- ninety.io pricing should be researched before finalizing — the initial assumption that it's "too expensive" hasn't been verified.
