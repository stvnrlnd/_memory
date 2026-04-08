# sendfeed.to — Overview

## What It Is

sendfeed.to is a bring-your-own-provider (BYOP) platform for sending RSS feed digest emails. Users organize one or more RSS feeds into a project, configure how often a digest should be sent, and the platform handles reading the feeds and delivering emails to subscribers on that schedule.

The defining characteristic is that users supply their own email credentials rather than relying on sendfeed.to's infrastructure to send mail. This keeps the platform lean and puts users in control of their own sending reputation and deliverability. The model is inspired by Laravel Forge — a tool that orchestrates interactions with providers rather than being a provider itself.

## Origin

The idea came from a personal problem: wanting to publish content via a Statamic site and automatically send digest emails to subscribers, without being forced to publish content through a third-party platform first. Existing solutions required content to live on their platform. sendfeed.to reads feeds from wherever they already live.

## Target Audience

- **Primary:** Small blog operators who want a set-it-and-forget-it digest email solution so they can focus on writing, not infrastructure.
- **Secondary:** Anyone who wants to collect and distribute RSS feeds — whether sending curated content to an audience or aggregating feeds for personal use or a small group.

## Core Concepts

- **Feed** — An RSS feed URL monitored for new content. Feed limits are counted across all of a user's projects (e.g. on the Growth tier, a user can have 5 feeds distributed across any number of projects).
- **Project** — A named grouping of one or more feeds. Digest frequency and subscriber list are configured at the project level.
- **Digest** — A periodic email compiled from new feed content, sent on the project's schedule. Frequency options: daily, weekly, or monthly.
- **Subscriber** — A recipient of a project's digest emails.

## Email Provider Support

Users connect their own SMTP credentials to send digest emails. Generic SMTP is the initial approach — the widest net. Direct API integrations with specific providers (Postmark, Mailgun, SES, etc.) are a future consideration, not in scope for MVP.

## Authentication

Email and password for MVP. Social login and magic links are not in scope initially but are not ruled out for the future.

## Status

In development. No production deployment yet. The code in `_sites/sendfeed_to/` represents all work done so far. A marketing page or two is a sensible early milestone before launch.

---

## Further Reading

- [Pricing](pricing.md)
- [Tech Stack](tech-stack.md)
- [Roadmap & MVP Scope](roadmap.md)
- [User Flows](user-flows.md)
- [Marketing Positioning](positioning.md)
- [Competitive Landscape](competitive-landscape.md)
- [Free Trial & Onboarding](onboarding.md)
- [Revenue Forecast](revenue-forecast.md)
- [Changelog](changelog.md)
