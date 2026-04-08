# sendfeed.to — User Flows

Status annotations: **[Built]** = implemented, **[Pending]** = not yet built.

---

## 1. Registration & Onboarding

1. User lands on marketing site, clicks sign up **[Built]**
2. Fills in name, email, password **[Built]**
3. Receives email verification link **[Built]**
4. Verifies email **[Built]**
5. Redirected to plan selection — chooses Starter, Growth, or Pro **[Built]**
6. Enters payment details via Stripe **[Built]**
7. Lands on app dashboard **[Built]**

**Notes:** No free trial currently exists. Users must select a paid plan before accessing the app. Whether a trial period should be added is an open question (see `roadmap.md`).

---

## 2. Creating a Project

1. From the dashboard or Projects list, clicks "New Project" **[Built]**
2. Enters project name and optional description **[Built]**
3. Project is created; user is taken to the project detail view **[Built]**
4. Uploads a project logo (optional) **[Built]**

---

## 3. Configuring a Project

From the Project Settings page:

1. Sets send frequency: daily, weekly, or monthly **[Built]**
2. Sets send day (for weekly/monthly) and send time **[Built]**
3. Chooses mail driver: SMTP, Mailgun, Postmark, or Resend **[Built]**
4. Enters mail driver credentials (stored encrypted) **[Built]**
5. Sets From Name, From Address, and optional Reply-To **[Built]**

---

## 4. Adding Feeds

1. Navigates to the Feeds tab on the project **[Built]**
2. Enters an RSS feed URL **[Built]**
3. Feed is saved; title and description are stored alongside the URL **[Built]**
4. Can add multiple feeds up to the plan's feed limit **[Built]**

**Pending:** Feeds are not actually polled yet. The fetch job doesn't exist.

---

## 5. Subscriber Acquisition

There are four ways subscribers can be added to a project. All methods store the subscriber with unconfirmed status until the opt-in confirmation flow (flow #7) is complete.

---

### 5a. Manual Entry (via App Panel)

1. User navigates to the Subscribers tab on a project **[Built]**
2. Enters a subscriber's email address and saves **[Built]**
3. Subscriber is created; confirmation email should be sent **[Pending — confirmation email not yet built]**

Best for: adding known subscribers one at a time (e.g. migrating from another tool, or onboarding a specific person).

---

### 5b. CSV Import

1. User navigates to the Subscribers tab **[Built]**
2. Uploads a CSV of email addresses **[Built]**
3. Subscribers are bulk-imported **[Built]**
4. Confirmation emails should be sent to each **[Pending]**

Best for: migrating an existing subscriber list from another platform.

---

### 5c. Form Action Endpoint (FieldGoal-style)

Each project exposes a unique POST endpoint. The user points their own custom HTML form's `action` attribute at it — sendfeed.to handles the subscription, confirmation email, and duplicate checking behind the scenes.

1. User copies the project's form action URL from the app **[Pending]**
2. User builds their own subscribe form on their own site, pointing `action` at that URL **[Pending]**
3. Visitor submits their email on the user's site **[Pending]**
4. sendfeed.to receives the POST, creates the subscriber, sends a confirmation email **[Pending]**
5. Visitor is redirected back (or to a configurable success URL) **[Pending]**

Example form:
```html
<form action="https://sendfeed.to/subscribe/[project-handle]" method="POST">
  <input type="email" name="email" required>
  <button type="submit">Subscribe</button>
</form>
```

Best for: users who want full control over the subscribe form's design and placement on their own site.

---

### 5d. Hosted Subscribe Page

Each project gets a public subscribe page hosted on sendfeed.to — no custom form needed. The user links to it from their site, bio, or anywhere else.

1. User copies the hosted page URL from the app **[Pending]**
2. Visitor navigates to `https://sendfeed.to/subscribe/[project-handle]` **[Pending]**
3. Fills in their email and submits **[Pending]**
4. sendfeed.to creates the subscriber and sends a confirmation email **[Pending]**
5. Visitor sees a confirmation message **[Pending]**

The hosted page should show the project name and logo so it feels on-brand for the publisher.

Best for: users who want a zero-setup subscribe link they can share anywhere without touching code.

---

### 5e. Embeddable Form Widget

A small JavaScript snippet (or iframe fallback) that renders a subscribe form inline on any site.

1. User copies the embed snippet from the app **[Pending]**
2. Pastes it into their site's HTML **[Pending]**
3. The form renders inline on their page **[Pending]**
4. Submission is handled the same as the hosted form (5d) or form action (5c) **[Pending]**

Best for: users who want an embedded form without writing their own HTML.

---

## 6. Digest Delivery (Core Loop — Pending)

When a project's scheduled send time arrives:

1. Scheduler detects the project is due for a digest **[Pending]**
2. `FetchFeedJob` runs for each feed — polls the RSS URL, stores new items since `last_fetched_guid` **[Pending]**
3. `CompileDigestJob` gathers new feed items, builds the digest email **[Pending]**
4. Digest is sent via the project's configured mail driver to all active (confirmed, not unsubscribed) subscribers **[Pending]**
5. A `Digest` record is created with recipient count and sent timestamp **[Pending]**
6. Project's `next_send_at` advances to the next scheduled time **[Pending]**

---

## 7. Subscriber Opt-In & Unsubscribe (Pending)

**Opt-in confirmation:**
1. Subscriber is added (manually or via import) **[Built]**
2. Confirmation email sent with a signed URL **[Pending]**
3. Subscriber clicks the link, `confirmed_at` is set **[Pending]**
4. Subscriber begins receiving digests **[Pending]**

**Unsubscribe:**
1. Every digest email includes an unsubscribe link in the footer **[Pending]**
2. Subscriber clicks the link **[Pending]**
3. `unsubscribed_at` is set; subscriber stops receiving digests **[Pending]**
4. Subscriber can resubscribe (model method exists) **[Pending]**

---

## 8. Digest Preview (Pending)

1. User opens a project in the app **[Pending]**
2. Triggers a "Preview Digest" action **[Pending]**
3. A rendered version of the digest (using current feed content) is displayed in the browser **[Pending]**

---

## 9. Billing & Subscription Management

1. User visits the Billing page **[Built]**
2. Views current plan, subscriber count, and upcoming invoice **[Built]**
3. Toggles overage allowance (allow subscribers beyond plan limit to receive digests, billed at $1/1,000) **[Built]**
4. Clicks "Manage Billing" to open Stripe portal for plan changes, payment method updates, or cancellation **[Built]**

---

## 10. Login & Account Management

- Login with email and password **[Built]**
- Password reset via email **[Built]**
- Edit profile (name, email, password) **[Built]**
- Email change verification **[Built]**
