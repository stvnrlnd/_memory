## Intro
---
Are you anti- or pro-Godzilla?
## Metrics
---
-
## Since Last We Met
---
### Shawn K.
- [[2572-bug-promotion-level-not-showing]]
- [[2377-ai-tool-for-detecting-features]]
### Andre R.
- [[2343-plan-media-viewer-milestone-3]]
- [[2569-pdp-above-the-fold-simplification-gallery-mobile-ux-update]]
	- Working on above tasks together since related
### Craig B.
- [[2441-set-up-webpagetest-automation]]
	- Continuing with automated tests for search filters, moving to checkout
### Steven R.
- [[2526-customer-receipt-delivery-delay-notices]]
	- Moved to Review
- [[2571-state-page-landing-page-parameter-for-paid-ads]]
	- Plan to finish up today
- [[2449-mod-quote-request-save-feature]] On Hold
	- Taylor S. sent private slack message -- pushes LocalStorage, does not answers technical questions, uses AI code and Fathom recap in vaguely threatening way. See [[2025-12-16]] meeting notes, ref video.
	- Taylor: Put current work on ice and may circle back later, use AI code and may need to tweak
### Brian M.
- [[2075-css-framework]]
- [[2359-bulk-image-uploader-engineering-plan]]
	- Will finish today, then make new card
- [[2455-bug-similar-plans-slider]] In Review
- [[2466-update-tier-image-on-pro-services-page]] In Review
- [[2497-download-email-subject-line-and-dashboard-link]] In Review
- [[2129-group-order-history-events]] In Review
- [[1947-add-plan-tags-for-interior-photos-build-photos]] In Review
- [[2205-add-notes-section-in-the-back-end-for-build-photo-albums]] In Review
- [[2381-purchased-without-mods-report-adjustment]] In Review
- [[2561-designer-deliverable-download-file-name]] In Review
- [[2555-bug-wordpress-image-size]] In Review
### Taylor S.
- [[2578-add-front-tag-for-georgia-orders]]
- [[2299-research-send-users-text-updates-for-quotes-order-statuses]]
- [[2567-document-incident-report-scripts]] In Review
- [[2441-set-up-webpagetest-automation]] In Review
- [[2543-upgrade-to-php-85]] In Review
- [[2532-add-composer-update-to-php-install-script]] In Review
- [[2488-discount-scenarios]] In Review
## Rock Review
---
- [[2075-css-framework]] Brian M.
## Headlines
---
-
## Issues
---
- [[2396-search-facet-analytics-report-fixes-updates]]
	- revision points, on hold
	- will have Shawn spin up new elastic db for this data, probably add index limts
- [[2574-sanitize-query-parameters-for-save-this-search]]
	- Related to above
	- right now just sanitizing url string, but not being sanitized, can use snitized url for search facet analytics report
	- Tag Steven
- [[2582-elastic-server-for-analytics]]
	- Tag shawn
- [[2556-add-intro-content-to-state-page]]
	- couple of hardcoded paragraphs
- [[2535-demo-new-plan-ranking-algorithm]]
	- Taylor wants to work on with Shawn
	- Taking featured plans and reg plans, merging
- [[2570-require-pro-customers-to-sign-in-during-checkout]]
	- right now when matching email is found, login popup shows, but can dismiss
	- do not allow pro users to continue without logging in
	- not a lot of thought about what should say or when should happen
	- May try to use different email
	- !! security concern: exposing that account exists (Steven thinks, Taylor verbalizes -- Taylor finds it annoying when sites don't tell you if email/username was found and password was wrong)
	- pro users may never checkout as guest, all other users can checkout as guest
	- Taylor: "something weird that's niggling at the back of my mind about trapping customers in auth modal"
	- Brian: "maybe we can create a new frontend for pro users, same backend"
- [[2549-rich-snippets-review-card-faq-product]]
	- on product and search page, just need to review for google standards
	- goal is to get featured on google
-  [[200-order-revisions-before-releasing-to-designer]]
	- restart, a lot has changed about order process and a lot more changes are coming
	- should be rewritten as a minimal update that allows some db_operations functionality
- [[2521-accessibility-audit]]
	- Do accessibility audit, come up with 2-6point tasks that get most bang for buck
	- Probably a lot of AI fixes
	- Maybe a Craig task? Was moved to Craig
## Ratings
---
- Shawn K.:
- Andre R.:
- Craig B.:
- Brian M.:
- Taylor S.:
- Steven R.:

Average:
## Other Notes
---
- Shawn passing on today's meeting, sore throat
- AI notetaker does not keep personal conversation
- What's for lunch:
	- Taylor: ham and mustard (no bread)
	- Brian: fried rice (no mustard)
	- Steven: No lunch yet
	- Craig: making lunch, beef & fat-free cheese and spinach wrap
	- Andre: Tomato and orzo sausage soup (with mustard)
- Taylor S. van damaged by storm/limb
- Craig B. icy weather
- Brian M. snowy weather
- When you have a new card with new number and want to work from old work, make a note in the new card and make new branch from old branch with new card number -- Taylor/Brian filter by card number for branch