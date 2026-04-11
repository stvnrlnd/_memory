# homestead.plus — Overview

## What It Is

homestead.plus is a multi-vendor marketplace for house floor plans. Businesses list and sell floor plan products; customers browse, purchase, and organize those plans into build projects tied to specific properties. The platform also surfaces a directory of home-building professionals that customers can engage during their build journey.

The existing floor plan market (ABHP, The Plan Collection, etc.) is essentially a collection of file stores — customers buy a plan and are immediately on their own. homestead.plus treats the floor plan purchase as the beginning of the build journey, not the end: connecting it to a project, a team of professionals, and an ongoing relationship with the designer and platform.

Inspiration: America's Best House Plans (houseplans.net).

Domain: **homestead.plus** (registered, not yet in production)

---

## Business Model

- **Customers** — Browse the shop, purchase floor plans, and organize them into Projects. A project tracks the land address, chosen floor plan(s), and collaborating professionals.
- **Business profiles** — Any user can apply for a business profile. All businesses require admin approval before becoming active. A business profile is required to sell products, offer services, or appear in the professionals directory. Some businesses sell products (Designers), some offer services (Builders, Realtors, etc.), some do both.
- **Professionals directory** — Approved business profiles are surfaced in a searchable public directory. Not a transactional marketplace on the services side; it's a lead-gen layer. Organic discovery is the default; paid placements are a secondary revenue option.
- **Revenue** — 15% platform fee on product and service sales via Stripe Connect. 10% reduced rate available for qualifying businesses (conditions TBD). No subscription fee for businesses. See [Revenue Model](revenue-model.md).

---

## Current State (as of 2026-04-08)

**Done:**
- Database schema: profiles, products, projects, project_addresses, project_members, project_floor_plans, contacts
- Profile system: Customer/Business STI (level 1); architecture cleanup needed before building further
- Product system: FloorPlan STI; Statamic Runway integration
- Project system: model layer only, no UI
- Public shop: list + detail views
- Professionals directory: list + detail views
- Filament app panel: auth, multi-tenant by profile, business registration, profile settings
- Filament admin panel: scaffolded, resources TBD

**Architecture cleanup needed before building further (see roadmap Phase 0):**
- Add `business_type` column; implement Business subtype STI; add `commission_rate` column
- Remove `businessType` from `data` JSON; rename `studio_id` → `business_id` on products
- Add `ProductVariant` and `AddOn` models

---

## Key Decisions

- **Designer, not Architect or Studio** — anyone who creates or modifies floor plans is a Designer (matching ABHP's industry convention). Licensed architect status is a profile credential, not a separate business type.
- **Any approved business can sell products** — authorization is approval-based, not business-type-based.
- **Product variants** — each product has designer-defined variants (e.g., 2BR vs. 3BR) with their own price, specs, and files. Related configurations are variants, not separate products.
- **Add-on products** — cost-to-build reports, material lists, etc. are linked to a floor plan variant but purchasable standalone by existing buyers.
- **Viewer-first file delivery** — files served in a browser viewer (PDF initially, CAD post-MVP); download is secondary and per-variant controlled by the designer. Raw file URLs never exposed to the browser.
- **Lead time** — services and certain products carry a lead time with a distinct order lifecycle (pre-auth billing, status progression from Pending through Delivered).
- **Teams/connections** — profiles form typed connections; acceptance required for mutual relationships (customer↔customer, employee↔business) but not one-way relationships (customer→business, partner endorsement).
- **Manual business approval initially** — admin reviews all applications; intended to be automated once volume warrants it.

---

## Further Reading

- [Data Model](data-model.md)
- [User Flows](user-flows.md)
- [Revenue Model](revenue-model.md)
- [Revenue Forecast](revenue-forecast.md)
- [Tech Stack](tech-stack.md)
- [Competitive Landscape](competitive-landscape.md)
- [Buyer Journey & Marketing Direction](buyer-journey.md)
- [Content & Marketing Strategy](content-strategy.md)
- [Growth & Early Adoption Strategy](growth.md)
- [Roadmap](roadmap.md)
- [Changelog](changelog.md)
