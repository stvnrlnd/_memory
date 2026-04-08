# sendfeed.to — Changelog

## Unreleased

Core digest loop (feed fetching, compilation, sending), subscriber confirmation flow, digest scheduling, digest preview, and production infrastructure are all pending. See `roadmap.md`.

## 2026-04-07 (Admin / Docs)

- Created `tech-stack.md` — full inventory of backend, frontend, and infrastructure
- Created `roadmap.md` — MVP scope, what's built vs. missing, and phased launch sequence
- Created `changelog.md`
- Created `user-flows.md` — all 10 user flows annotated with build status
- Created `positioning.md` — marketing positioning, messaging, and differentiation
- Created `competitive-landscape.md` — breakdown of 10 competitors with gap analysis
- Created `onboarding.md` — free trial recommendation, onboarding flow, conversion triggers
- Updated `user-flows.md` — expanded subscriber acquisition into 5 methods (manual, CSV, form action endpoint, hosted page, embeddable widget)
- Updated `roadmap.md` — added subscriber acquisition as Phase 4, renumbered subsequent phases
- Created `revenue-forecast.md` — 12-month projection across three scenarios with assumptions and key levers

---

## 2026-04-07

- Fixed dashboard charts

## 2026-04-06

- Updated Docker / Laravel Sail configuration

## 2026-03-18

- Added project logo support via Spatie Media Library
- Logo displayed in app header and will be included in digest emails

## 2026-03-17

- Added Stripe billing via Laravel Cashier
- Added plan selection step to the registration flow
- Added billing page (subscription status, invoices, overage toggle, Stripe portal link)

## 2026-03-15

- Added pricing tiers and features matrix to the marketing site (Statamic content collections)
- Pricing tiers linked to features; plan selection UI in app pulls from this content

## 2026-03-13

- Implemented email verification on registration
- Fixed auto-login after registration

## 2026-03-11

- Added info/tooltip context to dashboard chart widgets

## 2026-03-06

- Finished project settings page (send schedule, mail driver config, email from/reply-to)
- Built send scheduler component (frequency, day, time selection)

## 2026-03-05

- Improved subscriber moderation (confirm, unsubscribe, resubscribe actions in the panel)

## 2026-03-03

- Updated database seeders and dashboard stats

## 2026-03-02

- Added Filament resources for Projects, Feeds, Subscribers, and Digests
- Full CRUD UI for all core entities in the app panel

## 2026-03-01

- Set up app panel styling and top navigation layout
- Added separate Statamic CP guard (isolates CMS auth from app auth)
- Added project send frequency enum with display labels
- Refined project creation workflow and permissions

## 2026-02-28

- Added Subscriber model with confirmation/unsubscribe/resubscribe logic

## 2026-02-24 – 2026-02-25

- Added Feed model with RSS URL tracking and last-fetched state
- Added Digest model
- Installed and configured npm dependencies (Alpine.js, Tailwind CSS v4, Vite)

## 2026-02-23

- Initial project setup: fresh Statamic site as the base
- Installed Laravel Boost, Filament, Tighten Parental
- Added Project model with user relationship and seeders
