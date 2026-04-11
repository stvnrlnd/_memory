# homestead.plus — Content & Marketing Strategy

## Philosophy

The platform launches before it has supply. The content strategy exists to:
1. Build SEO equity and an audience before designers are ready to list
2. Demonstrate platform value to prospective designer partners (show, don't tell)
3. Give customers real, free value so they associate homestead.plus with expertise — not just a storefront

Everything here should be genuinely useful. No fluff, no filler.

---

## Content Pillars

### 1. Informational Pages (Evergreen)

Dedicated pages explaining the home-building process — who's involved, what's needed at each stage, what questions to ask. High SEO value; establishes homestead.plus as an authoritative guide, not just a marketplace.

**Planned pages:**
- The build journey: From floor plan to move-in (anchors the buyer-journey.md framework)
- What do I actually need to give my builder?
- What does "permit-ready" mean, and do I need it?
- Floor plan file formats explained (PDF vs. CAD vs. DXF)
- How to read a floor plan
- Professional types explained: Designer, Architect, Builder, GC, Realtor — who does what and when to hire them (each gets its own page; double duty as directory landing pages per profession)

### 2. Blog

Ongoing content combining editorial, tips, and spotlight pieces. Not a dump of SEO articles — quality over quantity.

**Content types:**
- Tips & tricks (for buyers, for designers)
- Designer spotlights (see growth.md)
- Build journey stories
- How-to guides
- Industry perspective (things Steven knows from working at ABHP that aren't documented anywhere well)

### 3. Designer Spotlights

See `growth.md` for full strategy. In brief: high-quality editorial features on individual designers — their background, philosophy, and plans — published on the homestead.plus blog. Serves as early adopter acquisition (designers trade early participation for promotion) and SEO content.

### 4. Downloadable Guides & Templates

Free, gated (email capture) or ungated resources. Perceived value is high; production cost is low.

**Planned guides:**
- First-Time Home Builder's Checklist — from lot purchase to breaking ground
- How to Read a Floor Plan — symbols, notations, dimensions explained
- Questions to Ask Your Builder Before Signing
- What Floor Plan Files Do You Actually Need? — matches buyer journey delivery tier framing

**Planned templates:**
- Build project budget spreadsheet
- Contractor comparison worksheet
- Project timeline template

### 5. Interactive Tools

Higher effort but very sticky. Free to use; natural lead-in to browsing plans or contacting professionals. These are the highest-leverage pre-launch investments — nothing like them exists in this space.

**Planned tools:**

#### Style Quiz / Floor Plan Finder
Answer 8–10 questions (household size, lifestyle, lot type, style preference, budget range, must-haves) → matched to floor plan styles and characteristics. Lead gen machine; highly shareable. No comparable tool exists on any competitor site.

#### Lot Feasibility Checker
Enter lot dimensions → see which floor plan size ranges could realistically fit, with notes on setbacks, coverage ratios, and what questions to ask a local professional. Builders and buyers search for this constantly and find nothing useful.

#### Budget Range Estimator
Rough cost-to-build calculator: sq ft × regional cost index × finish level = ballpark range. Framed clearly as a rough estimate, not a quote. Links naturally to the professionals directory (connect with a builder for a real number).

**Note on in-house floor plans:** Not planned for early stage. May revisit in the future once the platform has established supply and brand identity.

---

## Prioritization

| Initiative | Value | Effort | Priority |
|---|---|---|---|
| Informational pages (buyer journey, professional types) | High | Low–Medium | High |
| Blog setup + first posts | High | Low | High |
| Designer Spotlight series | High | Medium | High |
| Downloadable guides | Medium | Low | Medium |
| Templates | Medium | Low | Medium |
| Style quiz / floor plan finder | Very High | High | Medium |
| Lot feasibility checker | High | Medium | Medium |
| Budget range estimator | High | Medium | Medium |

---

## Technical Notes

- Blog and informational pages live in Statamic (collections + entries)
- Interactive tools are likely Alpine.js components — consistent with the stack, no additional dependencies needed for the quiz and estimator; lot checker may need a simple calculation layer
- Downloadable guides served as PDFs; no complex delivery needed pre-launch
- Gating downloads behind email capture is optional — consider ungated for trust-building, gated later once email list has strategic value
