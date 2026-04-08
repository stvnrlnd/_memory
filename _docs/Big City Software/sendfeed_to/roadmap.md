# sendfeed.to — MVP Scope & Roadmap

## What MVP Means Here

MVP is the minimum needed to charge a real customer money and have the product actually deliver on its promise: feed content shows up in subscribers' inboxes on schedule, reliably, using credentials the user brought themselves.

---

## What's Already Built

The foundation is solid. Authentication, billing, and the full management UI are done.

**User & Billing**
- Registration, login, email verification, password reset, profile editing
- Stripe subscription billing (Cashier) — plan selection, billing portal, overage toggle
- Subscription requirement enforced before accessing the app

**Project & Feed Management**
- Full CRUD for projects, feeds, and subscribers via Filament panel
- Per-project send schedule (frequency, day, time)
- Per-project mail driver config (SMTP, Mailgun, Postmark, Resend) with encrypted credential storage
- Project branding (logo upload)
- Subscriber CSV import/export
- Dashboard with subscriber growth and digests sent widgets

**Marketing Site**
- Statamic-backed site with pricing tiers and features matrix defined in content collections
- Plan selection UI in the app pulls from this content

---

## What's Missing for MVP

These are the gaps that prevent the product from actually working end-to-end.

### 1. Feed Fetching
No queue jobs exist to poll RSS feeds. There's no feed items table — the `feeds` table only tracks `last_fetched_guid` and `last_fetched_at`. Need:
- A `feed_items` table to store fetched entries (guid, title, url, published_at, feed_id)
- A `FetchFeedJob` queued job that reads the RSS URL, compares against `last_fetched_guid`, and stores new items

### 2. Digest Compilation & Sending
No mailable classes or dispatch logic exist. Need:
- A `CompileDigestJob` that gathers new feed items since the last digest, builds an email, and sends it via the project's configured mail driver
- A `Digest` record created per send with recipient count
- Mailable + Blade/Antlers email template for the digest format

### 3. Digest Scheduling
The scheduling config is stored but nothing triggers it. Need:
- A Laravel scheduled command (runs every hour or minute) that queries projects whose `next_send_at` is due and dispatches `CompileDigestJob`
- Logic to advance `next_send_at` after each send

### 4. Subscriber Confirmation Flow
The `confirmed_at` and `unsubscribed_at` columns exist on the `subscribers` table and the model has `confirm()` / `unsubscribe()` methods, but no emails or routes back these up. Need:
- A confirmation email sent on subscribe with a signed URL
- A confirmation endpoint that sets `confirmed_at`
- An unsubscribe endpoint (linked from every digest footer) that sets `unsubscribed_at`
- Only confirmed, non-unsubscribed subscribers should receive digests

### 5. Subscriber Acquisition Methods

The current app supports manual entry and CSV import. Three additional acquisition methods are needed:

- **Form action endpoint** — A public POST route per project (e.g. `POST /subscribe/{handle}`) that accepts an email, creates the subscriber, and sends a confirmation. Users point their own `<form action="...">` at it. Needs: configurable success/error redirect URLs, CSRF exemption, honeypot spam protection.
- **Hosted subscribe page** — A public page at `/subscribe/{handle}` that renders a branded subscribe form (project name + logo). Submits to the form action endpoint. Needs: Statamic or Laravel route, minimal Blade/Antlers template.
- **Embeddable form widget** — A JS snippet (and/or iframe) the user pastes into their site. The iframe points to the hosted subscribe page. The JS version could submit via fetch to avoid a page redirect.

All three feed into the same confirmation email flow (flow #7 in user-flows.md).

### 6. Digest Preview
Users have no way to see what a digest will look like before it sends. A simple "preview" action in the app that renders the compiled digest in the browser would significantly reduce anxiety around setup.

### 6. Marketing / Landing Page
The Statamic content exists but it's unclear whether the public-facing site is built out. At minimum: a homepage that explains what sendfeed.to does and links to signup. One page is enough to launch.

### 7. Production Infrastructure
Laravel Sail is for local dev only. Need a deployment target with:
- A server running PHP 8.5, MySQL 8.4, Redis
- Queue worker running persistently (Supervisor or similar)
- Laravel Scheduler configured (cron)
- Mail credentials for transactional emails (confirmation, auth flows — separate from user's own SMTP)

---

## Suggested Launch Sequence

| Phase | Work | Goal |
|---|---|---|
| **1 — Core Loop** | Feed items table + FetchFeedJob + CompileDigestJob + send via project mail driver | First real digest delivered end-to-end |
| **2 — Scheduling** | Scheduled command + next_send_at advancement | Digests send automatically on schedule |
| **3 — Subscriber Flow** | Confirmation email + confirm/unsubscribe endpoints | Only opted-in subscribers receive mail |
| **4 — Subscriber Acquisition** | Form action endpoint, hosted subscribe page, embeddable widget | Users can grow their list without touching the app |
| **5 — Polish** | Digest preview, error handling on failed fetches/sends | Product feels trustworthy |
| **6 — Marketing** | Homepage live, signup CTA working | Can start directing people to it |
| **7 — Infrastructure** | Production server, queue worker, scheduler, SSL | Publicly accessible, actually running |

Phases 1–3 are the blocker. Nothing works without them. Phases 4–6 are about being ready to charge real people.
