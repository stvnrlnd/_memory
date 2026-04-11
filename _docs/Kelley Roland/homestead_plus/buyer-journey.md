# homestead.plus — Buyer Journey & Marketing Direction

## The Core Insight

The existing floor plan market treats the purchase as a transaction: customer pays, customer gets files, customer is on their own. Most customers don't know what they actually need — not which plan, not what format, not what comes next. The industry has never bothered to explain it clearly.

homestead.plus's competitive edge is treating the floor plan purchase as the **beginning** of the build journey, not the end. That starts with making the journey itself legible.

---

## The GitLab Parallel

GitLab's marketing presents every stage of the software development lifecycle as a selling point — Plan, Create, Verify, Package, Deploy, Monitor — and shows exactly where GitLab lives in each. Most developers already knew the workflow; GitLab just made it a narrative.

homestead.plus has a bigger opportunity: our customers often *don't* know the workflow at all. We're not just fitting into a known process — we're the ones who explain it. That creates trust and positions the platform as an expert guide, not just a storefront.

This framing should inform both marketing pages and editorial content (blog, guides, resource hub).

---

## The Build Journey (draft)

A first-time home builder's path, from dream to move-in. homestead.plus surfaces clearly where it lives in each stage — and what it hands off.

| Stage | What the Customer Needs | Where homestead.plus Fits |
|---|---|---|
| **1. Dream & Inspiration** | Ideas, reference, possibility | Browse floor plans; save favorites; understand what's achievable |
| **2. Choose a Plan** | The right floor plan for their life and lot | Shop by style, size, layout; compare variants; request modifications |
| **3. Customize** | Modifications to make the plan theirs | Request modifications from the Designer; track the design order |
| **4. Get Builder Quotes** | A plan a contractor can price from | Download the Builder Package (PDF + CAD); connect with Builders in the directory |
| **5. Permits** | Plans that meet local requirements | Understand what's needed; platform guidance on jurisdiction requirements; connect with local professionals |
| **6. Break Ground** | A team, a timeline, a build | Use the Project to track collaborators (builder, architect, realtor, etc.) |
| **7. Move In** | Done | — |

homestead.plus owns stages 1–4 directly, and facilitates 5–6 via the professionals directory and project tooling.

---

## Delivery Tiers (Product Packaging Idea)

A key friction point is that customers don't know what format they need. Rather than exposing raw file types, the platform should frame delivery in terms of *what stage they're in*:

- **Visualization Package** — PDF floor plan + rendered images. Enough to fall in love with a plan, show family, and dream. Not intended for construction.
- **Builder Package** — PDF + CAD/DXF files. What you hand a general contractor for a quote. The standard working set.
- **Permit Package** — Jurisdiction-ready drawings (varies by location). Platform can surface guidance on what's typically required and connect customers with professionals who handle permit submissions.

Studios/Designers list which packages they offer per variant. Customers self-select based on where they are in the process. The platform educates them at the point of purchase on what each package is for — frictionless because they're choosing a stage, not a file format.

This also means the viewer question is naturally tiered: a Visualization Package may only need PDF viewing; a Builder Package may warrant CAD viewing down the road.

---

## Marketing & Content Implications

- **Homepage / hero section** — Lead with the journey, not just the catalog. Something like "From floor plan to front door" as a through-line.
- **Product detail pages** — Surface which stage each package is designed for ("Ready to share with your builder? Get the Builder Package.").
- **Marketing pages** — Dedicated pages explaining each stage of the build process, how floor plans fit in, and what professionals are involved. High SEO value; establishes homestead.plus as the authority.
- **Blog / Resource Hub** — "What do I hand my builder?" / "Do I need an architect or a designer?" / "What does permit-ready actually mean?" — these questions are asked constantly and barely answered well anywhere. High-value content that converts.
- **Professionals directory** — Each professional type (Builder, Architect, GC, Realtor) gets a marketing page explaining what they do in the build process and when to hire them. Drives directory value and organic traffic.

---

## Notes

- Reference: ABHP (America's Best House Plans / houseplans.net) presents as white-glove but relies on designers to fulfill orders — customers often don't know what they're getting or what they need next. This is the gap homestead.plus can own.
- The delivery tier idea affects both the product data model (variant file types, package bundles) and the purchase flow UI. Worth revisiting when building out the product variant and checkout work.
