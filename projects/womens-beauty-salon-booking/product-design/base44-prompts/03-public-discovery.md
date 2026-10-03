# Prompt 03 — Public Discovery

## Objective

Build the approved public discovery experience for the Persian/RTL **single-location women’s beauty salon booking product**.

This step should make it easy for a first-time customer to understand what the salon offers, compare relevant services and specialists, recognize fixed-price vs approximate-price vs consultation-required services, and enter the booking journey with the correct service/specialist context preserved.

Build these approved public surfaces:

- Home
- Services list
- Service detail template
- Specialists list
- Specialist profile template
- About salon and contact

Preserve Prompt 00 foundation, Prompt 01 design system and Prompt 02 application shell/navigation.

Do **not** implement the full booking/payment journey, customer account, salon operations or manager controls in this step. Booking CTAs should enter the prepared booking destination with the correct context, but Prompt 04 owns the complete booking flow.

## Product context to preserve

This product represents one physical women’s beauty salon in Iran.

Public discovery exists to help customers answer practical questions before booking:

- What service do I need?
- What does it generally cost?
- Is the price fixed or approximate?
- How long does it take?
- Does duration depend on a relevant volume option?
- Which specialists provide it?
- Can I book it directly, or does it require consultation first?
- If I start from a specialist, which supported services can I actually book with that specialist?

Do not turn discovery into marketplace browsing. There are no branches, competing salons, independent providers, marketplace ratings, location filters or at-home worker selection.

Each future appointment contains exactly one service and one eligible specialist.

## Public shell and navigation

Use the public shell from Prompt 02 without redesigning it.

Approved primary navigation remains:

- `خدمات`
- `متخصص‌ها`
- `درباره سالن و تماس`
- `نوبت‌های من`

Primary CTA remains:

- `رزرو نوبت`

Keep the temporary demo salon identity `سالن نمونه` clearly replaceable. Do not invent a final brand name, logo, slogan, credentials or marketing claims.

The public experience is Persian and RTL, mobile first, and uses the approved warm ivory / white / deep-plum design system.

## Shared demo data

Use the coherent fixtures created in Prompt 00 rather than creating unrelated page-specific examples.

The public data model must support at least:

1. One directly bookable fixed-price service with fixed duration.
2. One directly bookable approximate-price service whose booking duration varies by a manager-defined volume option.
3. One consultation-required service that does not pretend to support direct booking.
4. At least three fictional demo specialists with overlapping service eligibility so both service-first and specialist-first discovery make sense.

All public demo data must remain internally consistent with later booking/calendaring behavior.

Do not invent ratings, review counts, awards, certifications, years of experience, customer counts, “best salon” claims or before/after proof.

If sample photography is used, make it clearly illustrative/demo content rather than representing it as verified salon staff, premises or results.

## P01 — Home

Build a useful product home page, not a decorative marketing-only landing page.

The home page should quickly establish:

- temporary salon identity,
- concise description of the salon/service offering,
- direct `رزرو نوبت` action,
- clear entry to services,
- clear entry to specialists,
- a concise contact/location section using demo-safe content,
- enough practical information that the next action is obvious.

### Home hierarchy

Prioritize useful action over decoration.

A recommended hierarchy:

1. Clear hero/introduction with one dominant `رزرو نوبت` CTA.
2. Featured/service-entry section using actual shared service fixtures.
3. Specialist discovery section using actual shared specialist fixtures.
4. Concise explanation of how booking works at a high level, without implementing the booking flow.
5. Salon/contact context.
6. Footer with the approved public navigation/support links.

Keep the hero calm and refined. Do not allow an oversized image/headline to push the main booking/service choice far below the first practical screen.

Do not add:

- testimonials,
- star ratings,
- animated counters,
- fake trust badges,
- gallery as a new product requirement,
- blog/articles,
- promotions/coupons,
- newsletter signup,
- ecommerce products,
- social proof invented only to fill space.

If a small illustrative image is used, it supports the salon context and never implies verified results.

## P02 — Services list

Build a services discovery surface that helps customers choose correctly.

Each service card/list item should show the information needed to decide whether to open the detail:

- service name,
- concise description/category context when useful,
- fixed or approximate price wording,
- relevant duration summary,
- whether a volume choice affects duration,
- direct-bookable vs consultation-required status,
- relevant primary action.

### Price wording

For genuinely fixed-price services, use clear fixed-price wording.

For variable-price services, do not present the demo basis as a guaranteed final price. Use the approved concept such as:

- `قیمت تقریبی مبنای بیعانه`

and make it clear on detail that the final price is agreed before the service begins.

For consultation-required services, do not show a misleading `رزرو نوبت` CTA. Use a contact/consultation action instead.

### Grouping and filtering

Do not invent complex category/filter systems unless the actual shared demo catalog needs simple grouping for clarity.

This is one salon with a manageable catalog, not a marketplace search product.

Avoid:

- location filters,
- price sliders,
- rating filters,
- branch filters,
- provider marketplace sorting,
- “recommended for you” personalization.

## P03 — Service detail template

Create one reusable service-detail template for all services.

The page should answer:

- What is this service?
- Is it directly bookable?
- Is the price fixed or approximate?
- What price factors matter?
- What duration applies?
- Does the customer need to select a volume option later?
- Which specialists are eligible?
- Is consultation required?
- What is the next valid action?

### Required content

Show, when relevant:

- service name,
- clear description,
- fixed or approximate price basis,
- duration information,
- volume-option explanation where duration varies,
- relevant price factors without fake precision,
- prerequisites/consultation requirement,
- eligible specialist summaries,
- booking/contact CTA,
- link back to services.

Do not expose manager/internal configuration language to customers.

### Directly bookable service

For a directly bookable service:

- provide `رزرو نوبت`,
- entering booking must preserve the selected service,
- if volume is required, Prompt 04 will ask for the appropriate volume choice before availability,
- show eligible specialists so the customer understands who may provide the service.

Do not select a specialist silently from the detail page unless the customer explicitly starts from one.

### Consultation-required service

For a consultation-required service:

- do **not** provide a misleading direct booking CTA,
- show why the next step is contacting the salon in concise customer language,
- provide the approved salon-contact path,
- do not invent a consultation booking subsystem unless explicitly approved later.

### Approximate-price service

For variable-price services:

- distinguish the disclosed approximate booking/deposit basis from the eventual final price,
- explain that the final price is accepted before service starts,
- if volume affects booking duration, explain that volume changes reserved duration and therefore later availability,
- do not imply that changing the volume automatically changes the disclosed usual-volume deposit basis unless approved product data explicitly says so.

## P04 — Specialists list

Build a simple salon-specialist discovery surface.

Each specialist card should include:

- specialist name,
- honest demo portrait or approved neutral fallback,
- concise neutral bio/expertise summary,
- supported services,
- action to view the specialist profile.

Do not show fabricated ratings, review counts, badges, rankings or “top specialist” labels.

Do not present specialists as independent marketplace vendors with separate businesses, pricing systems or checkout flows.

Specialists belong to this salon and their public role is to help customers understand expertise and supported services.

## P05 — Specialist profile template

Create one reusable specialist-profile template.

The profile should include:

- name,
- demo portrait/fallback,
- concise professional demo bio,
- supported services,
- clear service-to-booking actions,
- link back to specialists.

### Specialist-first booking entry

A customer starting from a specialist must choose a service that specialist actually supports.

When the customer selects a supported service and enters booking:

- preserve the named specialist preference,
- preserve the selected service,
- do not ask the user to rediscover that specialist unnecessarily in Prompt 04,
- later availability must still validate that the named specialist is eligible and free for the full duration.

Do not show a generic `رزرو با این متخصص` action if it can lead to a service the specialist does not provide. The supported service relationship must remain explicit.

## Service ↔ specialist cross-links

Public discovery must make the approved two-way relationship useful:

- Service detail → eligible specialists.
- Specialist profile → supported services.

Cross-links should preserve useful context and avoid dead ends.

Examples:

- From a service page, selecting a specialist can lead to their profile while retaining an obvious path back to/book that service.
- From a specialist profile, selecting a supported service can enter booking with both service and named specialist preference preserved.

Do not create contradictory eligibility information between service and specialist pages.

## P06 — About salon and contact

Build one combined `درباره سالن و تماس` surface.

Do not split it into separate thin About and Contact pages.

Include only useful content:

- concise salon introduction,
- demo-safe location/address context clearly marked as sample if not real,
- working/contact information only if supplied by shared demo fixtures and clearly sample,
- route/directions context when meaningful,
- general booking-policy explanation at a high level,
- consultation/support contact path,
- `رزرو نوبت` action.

Do not fabricate a real phone number/address and present it as verified operational information.

General policy copy is explanatory only. The terms stored/reviewed for an actual booking later remain authoritative.

Salon contact must not be presented as:

- proof of account ownership,
- automatic policy exception,
- guaranteed refund route,
- substitute for required customer acceptance,
- method for bypassing the booking rules.

## Booking entry behavior

This prompt does not build the booking flow, but every public booking entry must pass coherent context into the prepared booking container from Prompt 02.

Support these entry patterns:

### General booking CTA

`رزرو نوبت` from Home/header/contact can enter booking with no service preselected.

Prompt 04 will start at service selection.

### Service-first entry

`رزرو نوبت` from a directly bookable service detail preserves:

- selected service.

Prompt 04 may then request volume if relevant, then specialist/time.

### Specialist-first entry

Booking from a specialist profile preserves:

- selected specialist,
- selected supported service.

Prompt 04 should respect the named preference rather than discarding it.

### Consultation service entry

A consultation-required service must route to salon contact rather than a fake booking path.

## Public availability hints

Public discovery may state that availability will be checked during booking, but do not build a fake availability calendar in this step.

Do not show arbitrary “available today” badges unless they come from the shared coherent fixture and Prompt 04 can honor them.

Avoid promises such as:

- “instant confirmation” when deposit/payment is still required,
- “available now” without full-duration validation,
- “booked” before payment confirmation.

## Visual direction

Use the approved design system and visual direction:

- calm,
- professional,
- warm,
- refined,
- honest.

Public discovery can be more spacious and photographic than booking/operations, but it must remain practical.

Use:

- warm ivory page canvas,
- white surfaces,
- deep-plum primary actions,
- pale-rose accent sparingly,
- Vazirmatn,
- moderate radii,
- restrained borders/shadows,
- one dominant CTA per task.

Avoid:

- black-and-gold luxury clichés,
- saturated pink everywhere,
- glitter/rose-gold effects,
- glassmorphism behind prices/actions,
- excessive gradients,
- decorative animation loops,
- giant ornamental typography that hides practical service information.

## Imagery rules

Service imagery uses a stable 4:3 treatment where appropriate.

Specialist portraits use a stable 1:1 treatment.

Use actual authorized salon imagery when later supplied. For now, any generated/sample imagery must remain clearly illustrative/demo content.

Do not use imagery to imply:

- guaranteed cosmetic results,
- actual salon premises when they are not,
- real employees when they are fictional demo fixtures,
- certifications/testimonials that were not supplied.

Provide neutral fallbacks so missing imagery never blocks discovery or booking entry.

## Responsive behavior

Public discovery is mobile first.

### Narrow screens

- use one-column service layouts,
- keep useful service/name/price/duration content before decorative material,
- let specialist cards use a second column only when labels remain comfortable,
- keep primary action reachable,
- wrap long Persian copy,
- avoid horizontally scrolling critical service information,
- do not allow images to dominate the first viewport,
- if a compact sticky booking/contact action is used after the original CTA scrolls away, it must mirror the same action/state and never cover content or later keyboard areas.

### Wider screens

- multi-column service/specialist cards are allowed,
- service/specialist detail may use balanced image + content layouts,
- maintain readable content width and hierarchy,
- do not stretch text into very wide unreadable lines.

Responsive adaptation must not remove services, specialists or actions available on desktop.

## Persian content and formatting

Use natural, respectful Persian and canonical terminology.

Use labels such as:

- `رزرو نوبت`
- `مشاهده خدمت`
- `مشاهده متخصص`
- `متخصص‌های این خدمت`
- `خدمات این متخصص`
- `تماس با سالن`
- `نیازمند مشاوره`
- `قیمت تقریبی مبنای بیعانه`

Use Persian digits for visible amounts where appropriate and label money as `تومان`.

Do not use lorem ipsum.

Long service/specialist names and descriptions should wrap. Never truncate essential identity, price type, duration or booking/consultation requirement simply to preserve card height.

## Local states in discovery

Use the reusable Prompt 01 components to support basic meaningful discovery states now, while Prompt 08 will perform the complete cross-product state/recovery pass.

At minimum distinguish:

- loading,
- actual empty catalog/eligibility result,
- known data-read failure,
- missing optional image,
- consultation-required / not-directly-bookable,
- temporarily invalid/incomplete demo configuration that prevents a misleading booking CTA.

Rules:

- Empty is not an error.
- A fetch/read failure must not look like “no services”.
- If required service price/duration/eligibility fixture data is invalid, do not invent a value just to keep a booking button enabled.
- Missing optional imagery uses fallback; it does not disable a real service.

## Accessibility and interaction

Preserve Prompt 01 accessibility rules:

- visible labels,
- visible focus,
- keyboard-operable cards/links/menus,
- minimum 44 px action target,
- no essential information on hover only,
- no color-only distinction,
- useful alternative text for informative imagery,
- decorative imagery uses empty alternative text,
- headings follow a meaningful hierarchy,
- repeated card actions have understandable accessible names.

Avoid turning entire complex cards into one ambiguous nested clickable region when they contain multiple actions.

## Prototype honesty

This public experience is a prototype using demo fixtures.

Never claim:

- real salon credentials,
- actual customer reviews,
- actual ratings,
- actual operating address/phone unless supplied,
- real-time authoritative availability before Prompt 04 demonstrates it,
- real SMS/payment/refund behavior,
- production-grade persistence/security.

The product can look polished without pretending demo information is verified business data.

## Do not add

Do not add during Public Discovery:

- marketplace/salon comparison,
- branch selection,
- home-service address/workforce dispatch,
- multi-service cart or bundles,
- ratings/reviews/testimonials,
- favorites,
- loyalty/wallet,
- chat,
- product ecommerce,
- gift cards,
- waitlist,
- personalized AI recommendations,
- blog/articles as a new scope area,
- promotions/coupons as a new capability,
- full availability calendar,
- SMS login implementation beyond prepared entry/access structure,
- deposit/payment/hold/result logic,
- customer appointment management,
- salon operations or management forms.

Do not change the approved business rules because a marketing template suggests different behavior.

## Acceptance check

Before considering this step complete, verify that:

- Home prioritizes clear service/specialist discovery and `رزرو نوبت` over decorative marketing;
- public navigation from Prompt 02 remains intact and visually consistent;
- Services list uses the shared coherent service fixtures rather than unrelated per-page content;
- fixed-price services are clearly distinguishable from approximate-price services;
- approximate-price copy does not guarantee the eventual final service price;
- a duration-varying service explains that the relevant volume choice affects booked duration/availability;
- consultation-required services route to salon contact and do not show a misleading direct-booking CTA;
- Service detail exposes only eligible specialists and can enter booking with the selected service preserved;
- Specialists list/profile show only supported services and no fabricated rating/review information;
- specialist-first booking entry preserves both named specialist preference and selected supported service;
- Service ↔ specialist cross-links remain mutually consistent;
- About/contact is one useful combined surface rather than thin duplicate pages;
- demo address/contact/media are never represented as verified real salon facts;
- all booking CTAs lead to the prepared booking destination but the full booking/payment workflow has not been implemented prematurely;
- discovery works clearly at narrow and wide widths with long Persian content;
- loading, empty and read-error states are distinguishable;
- missing images have useful neutral fallbacks;
- no marketplace, ratings, ecommerce, loyalty, wallet, chat, waitlist, blog or other deferred capability has been introduced;
- Prompt 00 product rules, Prompt 01 design system and Prompt 02 navigation/access boundaries remain intact.

Stop once the public discovery surfaces are coherent, cross-linked and ready to hand the selected context into the booking journey. Prompt 04 will implement booking, identity, hold, payment and result behavior.