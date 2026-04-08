# sendfeed.to — Competitive Landscape

## The Key Differentiator

No competitor currently offers a bring-your-own-email-provider (BYOP) model for RSS digest automation. Every tool in this space either sends on its own infrastructure or is a full publishing platform that happens to have RSS features. sendfeed.to is the only one that treats itself as an orchestrator — it polls feeds, compiles digests, and fires them through credentials the user already owns.

---

## Competitor Breakdown

### Blogtrottr
**What it is:** Free RSS-to-email service. Users subscribe their own inbox to feeds — it's designed for readers, not publishers with subscribers.

**Pricing:** Free (ad-supported). ~$19/year for ad-free.

**RSS-to-email:** Yes — native and primary feature. Real-time or interval-based delivery.

**BYOP:** No. Sends from Blogtrottr's infrastructure.

**Relevance:** High. Dominates the free, zero-friction RSS-to-email space. Risk is for users who just want to pipe a feed to themselves — but it doesn't support managing subscribers for others, which is sendfeed.to's actual use case.

---

### FeedBlitz
**What it is:** The most feature-complete RSS-to-email platform specifically built for bloggers and publishers.

**Pricing:** Starts at ~$1.49/month, scales with subscriber count. Three tiers: Core, Accel, Enterprise.

**RSS-to-email:** Yes — native. Supports immediate sends and curated digests (weekly, monthly).

**BYOP:** No. FeedBlitz sends from its own infrastructure. Higher tiers offer a transactional email API but it's not true BYOP — you're still going through FeedBlitz.

**Relevance:** High. Closest feature-equivalent. The key gap: no BYOP, and pricing scales per-subscriber.

---

### Buttondown
**What it is:** Lightweight, developer-friendly newsletter tool with solid RSS-to-email automation.

**Pricing:** Free up to 100 subscribers. $9/month up to 1,000. Scales from there.

**RSS-to-email:** Yes — 30-minute polling, configurable cadence (per-publish, weekly, monthly).

**BYOP:** No. Buttondown sends from its own infrastructure.

**Relevance:** Moderate. Very appealing to the developer/blogger audience sendfeed.to also targets. Differentiation is BYOP and the feed-aggregation (multi-feed) use case, which Buttondown doesn't emphasise.

---

### Kit (formerly ConvertKit)
**What it is:** Creator-focused email marketing platform with RSS automation built in.

**Pricing:** Free up to 10,000 subscribers (single automation). Creator plan: $39–$89/month.

**RSS-to-email:** Yes — auto-send emails when new blog content publishes, configurable frequency.

**BYOP:** No. Kit sends from its own infrastructure.

**Relevance:** Moderate. Appeals to the same creator audience, but Kit is full-featured email marketing — it's overkill for someone who just wants digest automation. BYOP remains the differentiator.

---

### Mailchimp
**What it is:** General-purpose email marketing platform. RSS campaigns are one of many features.

**Pricing:** Free tier (limited). $13–$350+/month depending on contacts and volume.

**RSS-to-email:** Yes — RSS campaigns with daily/weekly/monthly sends.

**BYOP:** No. Mailchimp sends from its own infrastructure.

**Relevance:** Low-moderate. Overkill for the target user. Complexity and pricing are the pain points that push people away. BYOP is irrelevant to Mailchimp's target customer.

---

### Beehiiv
**What it is:** Modern newsletter platform built for audience growth with monetization and analytics.

**Pricing:** Free up to 2,500 subscribers. Scale: $39–49/month. Max: $109/month.

**RSS-to-email:** Yes — but gated behind the Max tier ($109/month). Called "RSS-to-Send."

**BYOP:** No. Beehiiv sends from its own infrastructure.

**Relevance:** Low-moderate. Fast-growing but targets growth-focused publishers, not feed automators. The RSS feature being paywalled at $109/month is a genuine weakness sendfeed.to can exploit.

---

### Substack
**What it is:** Creator newsletter platform with a large built-in distribution network and monetization.

**Pricing:** Free to publish. Takes 10%+ of paid subscription revenue.

**RSS-to-email:** No native RSS-to-email. Substack publishes its own RSS feeds but doesn't ingest external ones.

**BYOP:** No.

**Relevance:** Low. Different product and audience. Substack is for building an audience from scratch on their network. Not relevant for someone with existing content elsewhere.

---

### Ghost
**What it is:** Open-source publishing platform with built-in newsletter/membership features.

**Pricing:** Self-hosted: free. Ghost Pro: $15–$199/month.

**RSS-to-email:** No native RSS automation.

**BYOP:** Partial — self-hosted Ghost can use any transactional email provider, but the managed version (Ghost Pro) only officially supports Mailgun. Not a true BYOP concept.

**Relevance:** Low. Different positioning entirely (full CMS + publishing). Of note: Ghost users who want digest automation for their existing Ghost RSS feed are a potential sendfeed.to customer.

---

### Blogtrottr vs. Follow.it vs. Kill the Newsletter (brief)

- **Follow.it** — Multi-channel content distribution for publishers. Not a focus on BYOP or digest automation. More of a publisher dashboard than a tool.
- **Kill the Newsletter** — Converts email newsletters *into* RSS feeds (opposite direction). Free, open-source, personal use only. Not a competitor.

---

## The Gap

| Capability | sendfeed.to | Blogtrottr | FeedBlitz | Buttondown | Kit | Beehiiv |
|---|---|---|---|---|---|---|
| RSS-to-email | Yes | Yes | Yes | Yes | Yes | Yes (Max tier only) |
| BYOP (your email credentials) | **Yes** | No | No | No | No | No |
| Multi-feed digest per project | Yes | No | Yes | No | No | No |
| Subscriber management | Yes | No (reader tool) | Yes | Yes | Yes | Yes |
| Flat-tier pricing | Yes | Yes | No | No | No | Yes |
| No platform lock-in | Yes | Partial | No | No | No | No |

The gap sendfeed.to fills is real and not clearly owned by anyone: **RSS-native digest automation with bring-your-own email provider, clean subscriber management, and no dependence on platform sending infrastructure.**

---

## Why Competitors Won't Copy This

Competitors monetize on sending volume or subscriber count. Adopting a true BYOP model removes that revenue lever. It's not a technical barrier — it's a business model conflict. That makes this a durable differentiator, not just a temporary one.

---

## DIY Risk

The most credible alternative isn't a competitor product — it's a Make or Zapier workflow: poll RSS → filter → compile → send via Mailgun. Technically possible but requires setup, maintenance, and debugging. sendfeed.to's value is that it's a finished, opinionated product that does this reliably, with subscriber management and a UI.

---

*Research conducted April 2026.*
