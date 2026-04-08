# sendfeed.to — Free Trial & Onboarding Conversion Plan

## Current State

There is no trial. Users must select a paid plan immediately after email verification. They hit Stripe before they've seen anything work. This is the highest-friction path possible — asking for money before delivering any value.

---

## The "Aha Moment"

The moment a user gets real value from sendfeed.to is the first time a digest lands in a subscriber's inbox. Everything before that — creating a project, adding credentials, adding feeds, adding subscribers — is setup cost, not value. The goal of onboarding is to get users to that moment as fast as possible, and make sure it happens before they're asked to pay.

---

## Trial Recommendation: 14-Day Free Trial, Card Required

**Recommended approach:** 14-day full-access trial with a credit card required at signup. No feature restrictions during trial.

**Why card-required over card-optional:**
- BYOP means the user has to do real setup work (SMTP credentials, RSS feeds, subscribers). Someone willing to do that setup is a serious lead — not a tire kicker. Card-required filters out casual browsers without meaningfully reducing qualified signups.
- Cashier supports trial periods natively with `trialDays()` — no significant engineering lift.
- Card-optional trials tend to generate high signup numbers and low conversion. For a niche tool like this, the inverse is better: fewer signups, higher conversion rate, better signal on what's working.

**Why 14 days (not 7 or 30):**
- 7 days is too short. The nature of digest email means a user might configure weekly sends — they'd only see one send during the trial. They need at least two to evaluate.
- 30 days is too generous. It reduces urgency and extends the sales cycle.
- 14 days gives room for a weekly digest user to send two digests, and a daily user to get real signal on deliverability and workflow.

**Why full-access (not feature-limited):**
- The product is simple enough that there isn't an obvious "premium only" feature to gate. Limiting feeds or subscribers during trial creates friction before the aha moment, defeating the purpose.

---

## Onboarding Flow

The current registration flow is: create account → verify email → select plan → enter payment → app dashboard.

With a trial, it becomes: create account → verify email → start trial (card required) → app dashboard → **guided setup**.

The guided setup is the new piece. Right now users land on a dashboard with no instruction. They need to be walked through the four steps that produce value:

**Step 1 — Create a project**
Give it a name, set a send schedule. This is quick and low-commitment.

**Step 2 — Add your email credentials**
Connect SMTP/Mailgun/Postmark/Resend. This is the BYOP moment — it's where sendfeed.to differs from everything else. The UI should make clear why this is a feature, not a burden: "Your emails come from your account, your domain, your sending reputation."

**Step 3 — Add a feed**
Paste an RSS URL. The app should validate it and show a preview of recent items so the user can see what will be in their digest.

**Step 4 — Add a subscriber (yourself)**
The first subscriber should be the user. Tell them explicitly: "Add your own email first — your next digest will arrive on schedule." This sets expectation and gets them emotionally invested in the outcome.

Once these four steps are complete, the app should show a clear "Your first digest will send on [date] at [time]" confirmation. That's the commitment moment.

---

## Conversion Triggers

The trial should be proactively managed, not passively counted down.

**Day 0 — Welcome email**
Sent immediately after trial starts. Subject: "You have 14 days — here's how to make the most of them." Contains the four setup steps above as a checklist with direct links.

**Day 1 — Setup nudge (if incomplete)**
If the user hasn't completed setup (no project, no feed, no subscriber), send a short prompt. Not a guilt trip — a single call to action: "Add your first feed."

**Day 3 — First digest confirmation (if setup complete)**
If the user has completed setup and has a scheduled send coming up, send a heads-up: "Your first digest sends in X days." Reinforces that value is coming.

**Day 7 — Mid-trial check-in**
"You're halfway through your trial. Here's what's happening in your account." Show stats: feeds connected, subscribers added, digests sent (if any). If nothing is set up, this is a re-engagement moment: "It only takes 5 minutes to send your first digest."

**Day 12 — Conversion prompt**
"Your trial ends in 2 days." Direct, no tricks. Show the plan they'll be on and what it costs. Include a link to manage/confirm billing. If they've sent at least one digest, call it out: "You've already sent X digests to Y subscribers."

**Day 14 — Trial ends**
Cashier handles the charge. If payment fails, account goes into grace — don't hard-lock immediately, give 3–5 days for a retry before restricting access.

---

## The Subscriber Overflow Mechanic as a Conversion Tool

The existing subscriber overflow design (subscribers can sign up past the plan limit, but won't receive digests) is already a good conversion trigger for growth. When a user hits their subscriber ceiling, the app should:

1. Surface a clear notification on the dashboard: "X subscribers can't receive your next digest."
2. Show the cost to fix it: "Add 1,000 subscribers for $1" or "Upgrade to Growth for $14/month."
3. Make the action one click.

This is a pull-based upgrade moment — the user has organic growth proving the product is working, which is the strongest possible motivation to pay more.

---

## Open Questions

- **Should there be a permanent free tier?** A single-feed, 100-subscriber free tier could drive top-of-funnel growth through word of mouth ("I use this free tool"). Risk: it cannibalizes Starter ($6/month) and creates a support burden from users who will never pay. Probably not worth it at this stage — revisit once there's revenue to subsidize it.
- **Annual billing?** A 15–20% discount for annual payment is standard and worth adding once monthly billing is stable. Not an MVP concern.
- **Referral program?** Users who love a simple tool like this will mention it. A lightweight referral credit (e.g., $6 account credit per referred paying customer) could be added later. Not MVP.
