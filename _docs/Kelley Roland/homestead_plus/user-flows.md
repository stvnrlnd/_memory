# homestead.plus — User Flows

Status: Draft — flows are defined at the conceptual level; detailed UX design is pending.

---

## Customer Flows

### Registration & Onboarding

1. Customer visits homestead.plus and clicks Sign Up
2. Enters name, email, password
3. Email verification sent → customer verifies
4. **Customer profile auto-created** (`UserObserver`) — no additional setup required
5. Customer lands in the app panel under their customer profile tenant
6. Optional: prompted to explore the shop or start a project

### Browsing the Shop (Public)

1. Visit `/shop` — browse floor plans (no account required)
2. Filter by style, bedrooms, bathrooms, sq ft range, stories, garage bays
3. Sort by newest or price
4. Click a floor plan → detail page with specs, images, teaser description, available variants and pricing
5. Select a variant (e.g., 2BR vs. 3BR) → see variant-specific price and specs
6. Add to cart or proceed to checkout (requires login)

### Purchasing a Floor Plan (Instant Delivery)

1. Select variant → checkout
2. **If designer requires a license agreement:** license is presented at checkout; customer must sign (checkbox + timestamp) before proceeding
3. Enter payment details (Stripe)
4. Payment captured → `Order` created with status `Paid`; signed license agreement recorded against the order
5. Redirected to order confirmation / viewer
6. Floor plan opens in the **in-browser viewer**
7. If designer has enabled download for this variant: PDF download button available
8. Order accessible from order history at any time; viewer available on re-open

### Purchasing a Service or Lead-Time Product

1. Select service or lead-time variant → checkout
2. Payment **pre-authorized** (not captured yet)
3. `Order` created with status `Pending`
4. Business receives notification of new order
5. Business accepts order → status moves to `Accepted`; customer notified
6. Business works on the deliverable → status moves to `In Progress`; customer notified
7. Business marks as `Ready for Review` → customer receives notification to review
8. Customer reviews; if satisfied, delivery is confirmed → status `Delivered`
9. **Pre-authorization captured** on delivery
10. Delivered files appear in viewer; order history updated

*Edge cases (TBD): customer requests revisions after Ready for Review, designer misses deadline, cancellation policy.*

### Viewing Purchased Plans

1. Go to Order History in app panel
2. See all purchases — instant-delivery and in-progress lead-time orders
3. Click a floor plan → opens in-browser viewer
4. Viewer prevents right-click save and browser-level file extraction
5. PDF download available if designer has enabled it for that variant
6. Purchase add-on products (cost-to-build report, material list) directly from this view if not already purchased

### Project Management

1. Create a new Project (name, optional description)
2. Add one or more addresses to the project (land parcels / build sites)
3. Assign a purchased floor plan variant to an address within the project
4. Manage project status: Planning → Active → Complete / Paused
5. Invite collaborators (project members):
   - Mutual connections (co-buyers) can be added directly
   - Others receive an email invite → account creation if needed → accept → added as member
   - Set access level: Manager or Viewer
6. View the project's full picture: address(es), assigned floor plans, team members

### Build Team

1. Browse the professionals directory or discover via preferred partner connections
2. Click "Add to Build Team" on a business profile — no acceptance required from the business
3. Build team visible on the customer's profile and optionally on specific projects
4. Optionally: associate a team member with a specific project (e.g., "This is my builder for Project X")

---

## Business Flows

### Registration & Application

1. User already has a customer profile (created on signup)
2. In the app panel, open the tenant menu → "Add Business Profile"
3. Select business type (Designer, Builder, GC, etc.)
4. Enter business name
5. Business profile created with `status = pending`
6. Confirmation shown: "We'll review your application and be in touch"
7. Email sent to both Steven (admin) and the applicant confirming receipt

### Approval (Admin Side)

1. Admin receives notification of new business application
2. Opens admin panel → business application queue
3. Reviews application details
4. Approves or rejects (with optional note)
5. Business owner notified by email of decision
6. On approval: business profile becomes active; owner can now switch to the business tenant

### Stripe Connect Onboarding

1. On first login to the business tenant after approval: prompted to connect Stripe account
2. Redirected to Stripe Connect onboarding (bank account, identity verification)
3. On completion: business can receive payouts from product/service sales
4. Products can be listed before Stripe Connect is complete, but orders won't pay out until connected

### Adding Products (Designer)

1. Switch to business tenant in app panel
2. Go to Products → New Floor Plan
3. Enter product details: title, style, specs (stories, bedrooms, bathrooms, sq ft, garage bays), teaser, images
4. Add one or more **variants**: for each variant — title, bedroom/bathroom/sq ft overrides, price, lead time (if applicable), download permission, upload deliverable file(s)
5. Optionally add **add-on products** linked to a variant (cost-to-build report, material list)
6. Save as Draft → review → Publish
7. Product appears in the public shop

### Managing Instant-Delivery Orders

1. New order notification received
2. Open Orders in app panel — order status is `Paid` (already fulfilled)
3. Files were delivered automatically to the customer at purchase
4. No action required unless there's a support issue

### Managing Lead-Time Orders

1. New order notification received
2. Open Orders — order status is `Pending`
3. Review order details; Accept (moves to `Accepted`) or decline with a note
4. Work on the deliverable — mark as `In Progress` when begun (customer notified)
5. Upload completed files to the order when ready
6. Mark as `Ready for Review` — customer notified to review
7. Customer confirms → status moves to `Delivered`; payment captured automatically
8. If revisions requested (TBD): order may return to `In Progress`

### Managing Business Profile & Directory Listing

1. Switch to business tenant
2. Go to Profile Settings
3. Edit: bio, city, state, phone, email, website, logo, photos
4. Profile is publicly visible at `/professionals/{handle}` when approved
5. Contact inquiries from the public profile appear in the app panel as `Contact` records; email notification sent on each new inquiry

### Preferred Partners

1. In the business app panel, browse the professionals directory
2. Find a partner business to endorse (e.g., a designer endorses a preferred builder)
3. Click "Add as Preferred Partner" — no acceptance required
4. Preferred partners appear on the business's public profile

---

## Flows TBD (Design Pending)

- Quoted service pricing (designer provides a quote; customer accepts before committing)
- CAD file viewer (post-MVP)
- Plan comparison
- Reviews and ratings
- Paid placement purchase flow (business buys a featured slot)
- Business internal team member invitation (mutual acceptance)
