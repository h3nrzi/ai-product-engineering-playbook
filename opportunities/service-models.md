# Service Product Model Taxonomy

This file defines the reusable **service-delivery / product models** that can be applied to the vertical families in [`service-products.md`](service-products.md).

The opportunity library now has two independent axes:

```text
Product Family (what service market?)
        +
Product Model (how is the service discovered, sold, scheduled, delivered, or managed?)
        ↓
Specific project opportunity
```

Example:

```text
Family: BEAUTY-SALON
Model: A01 Direct provider booking
Variant: Women's single salon
```

or:

```text
Family: BEAUTY-SALON
Model: M01 Open marketplace
Variant: Multi-salon marketplace
```

A project can combine multiple model IDs when the combination is meaningful, for example `A01 + S02` for direct appointment booking with a membership/credit plan.

The English websites below are **reference implementations**, not endorsements and not exact specifications for our projects. They are useful for studying real-world UX, business-model boundaries, and workflow patterns.

---

## A — Booking & provider scheduling

| ID | Model | What it means | Typical flow | English reference examples |
| --- | --- | --- | --- | --- |
| A01 | Direct provider booking | One service business exposes its own staff/services and availability | service → provider → slot → book | [Booksy](https://booksy.com/en-us), [Fresha](https://www.fresha.com/) |
| A02 | Multi-provider directory booking | Users compare many professionals and book a specific one | search → filter → provider → slot → book | [Zocdoc](https://www.zocdoc.com/), [Fresha](https://www.fresha.com/) |
| A03 | Multi-location / multi-branch booking | One brand operates several locations with shared discovery but local capacity | location → service → staff → slot → book | [Fresha](https://www.fresha.com/), [Booksy](https://booksy.com/en-us) |
| A04 | Consultation-first booking | A short consultation/assessment precedes the actual service | concern → consult → recommendation → treatment/service | [Zocdoc](https://www.zocdoc.com/), [LegalZoom](https://www.legalzoom.com/legal-services) |
| A05 | Waitlist / cancellation-fill booking | User joins a waitlist when capacity is unavailable | desired slot → waitlist → notification → accept | — |
| A06 | Walk-in / queue management | Service is primarily walk-in but users can see or reserve queue position | location → queue → check-in → service | — |

## M — Marketplaces & matching

| ID | Model | What it means | Typical flow | English reference examples |
| --- | --- | --- | --- | --- |
| M01 | Open service marketplace | Customer browses independent providers and chooses directly | need → providers → compare → hire/book | [Upwork](https://www.upwork.com/), [Rover](https://www.rover.com/), [Turo](https://turo.com/) |
| M02 | Managed marketplace | Platform controls more of matching, pricing, quality, or fulfillment | request → platform match → service → support | [Homeaglow](https://www.homeaglow.com/), [Taskrabbit](https://www.taskrabbit.com/) |
| M03 | Lead / quote marketplace | Customer submits a need and receives quotes or provider responses | request → leads/quotes → compare → hire | [Thumbtack](https://www.thumbtack.com/), [Bark](https://www.bark.com/en/us/) |
| M04 | Reverse-bid marketplace | Customer posts work; providers compete with offers | post task → offers → choose → deliver | [Airtasker](https://www.airtasker.com/us/), [Upwork](https://www.upwork.com/) |
| M05 | Curated / vetted expert network | Platform emphasizes screening and fit over open listing volume | intake → curated match → engage | [Zocdoc](https://www.zocdoc.com/), [Care.com](https://www.care.com/) |
| M06 | Any-provider / auto-assignment | User cares about service outcome more than named provider | service → availability → auto-assign → service | [Thumbtack](https://www.thumbtack.com/) |

## D — Dispatch & field service

| ID | Model | What it means | Typical flow | English reference examples |
| --- | --- | --- | --- | --- |
| D01 | On-demand dispatch | Nearby provider is dispatched immediately | request → match → ETA → service | [DoorDash](https://www.doordash.com/) |
| D02 | Emergency dispatch | High-urgency service with location, ETA, and rapid escalation | incident → location → dispatch → resolution | [AAA Roadside Assistance](https://www.acg.aaa.com/aaa-membership/roadside-assistance.html) |
| D03 | Scheduled field service | Technician visits a customer location at a chosen time | issue → details → schedule → technician visit | [Taskrabbit](https://www.taskrabbit.com/) |
| D04 | Route-based field service | Provider performs multiple geographically planned jobs per route/day | jobs → route → stops → completion/proof | — |
| D05 | Inspection-to-repair dispatch | Initial field inspection determines quote and follow-up work | issue → inspection → estimate → approve → service | [Thumbtack](https://www.thumbtack.com/) |

## S — Subscription, membership & recurring service

| ID | Model | What it means | Typical flow | English reference examples |
| --- | --- | --- | --- | --- |
| S01 | Recurring subscription service | Service repeats on a regular schedule | plan → recurring schedule → service → manage | [Homeaglow](https://www.homeaglow.com/) |
| S02 | Credit / pass membership | Monthly membership provides credits usable across services/providers | membership → credits → book → renew | [ClassPass](https://classpass.com/try) |
| S03 | Maintenance membership | Membership covers recurring maintenance plus priority/emergency support | asset → plan → maintenance → incidents | [AAA](https://cluballiance.aaa.com/) |
| S04 | Prepaid session package | Customer purchases a fixed bundle of sessions/uses | package → sessions → balance → renew | [ClassPass](https://classpass.com/plans) |
| S05 | Family / household membership | One payer manages services for multiple household members | account → members → services → shared management | [Care.com](https://www.care.com/) |

## P — Project, package & outcome-based services

| ID | Model | What it means | Typical flow | English reference examples |
| --- | --- | --- | --- | --- |
| P01 | Project + milestones | Work is scoped, contracted, and delivered across milestones | brief → proposal → contract → milestones → approval | [Upwork](https://www.upwork.com/) |
| P02 | Fixed-price service catalog | Service is pre-packaged with clear scope and price | browse package → requirements → buy → deliver | [Fiverr](https://www.fiverr.com/), [Upwork Project Catalog](https://www.upwork.com/services/) |
| P03 | Quote-first project | Scope is too variable for instant pricing | brief → estimate → approve → schedule/project | [Thumbtack](https://www.thumbtack.com/), [Bark](https://www.bark.com/en/us/) |
| P04 | Inspection / report product | Main deliverable is a professional assessment/report | asset/case → inspect → report → recommendations | — |
| P05 | Consultation-to-project | Paid/free consultation converts into a larger service engagement | consult → proposal → project → handoff | [LegalZoom](https://www.legalzoom.com/legal-services) |
| P06 | Success-fee / outcome-based service | Provider earns based partly or fully on achieved outcome | intake → eligibility → work → outcome → fee | — |

## R — Resource, space & rental models

| ID | Model | What it means | Typical flow | English reference examples |
| --- | --- | --- | --- | --- |
| R01 | Resource / venue reservation | User books a finite physical resource by time | need → resource → availability → reserve | [Peerspace](https://www.peerspace.com/) |
| R02 | Peer-to-peer rental | Individuals list assets for temporary use | search → asset → dates → reserve → return | [Turo](https://turo.com/), [Outdoorsy](https://www.outdoorsy.com/) |
| R03 | Rental + delivery/setup | Asset rental includes logistics or setup as part of service | asset → dates → delivery/setup → use → return | [Outdoorsy](https://www.outdoorsy.com/) |
| R04 | Rental + operator | Customer rents an asset together with a professional operator | asset/operator → schedule → service → close | — |
| R05 | Capacity / seat reservation | User reserves a seat/table/limited-capacity slot rather than a provider | capacity → time → party/seat → reserve | — |

## C — Case, document & concierge workflows

| ID | Model | What it means | Typical flow | English reference examples |
| --- | --- | --- | --- | --- |
| C01 | Case / document workflow | Service progresses through documents, reviews, and milestones | intake → documents → review → status → completion | [Boundless](https://www.boundless.com/services/individuals), [LegalZoom](https://www.legalzoom.com/) |
| C02 | Guided application / checklist | Product guides the user through a complex formal application | eligibility → checklist → forms → submit → track | [Boundless](https://www.boundless.com/services/individuals), [LegalZoom](https://www.legalzoom.com/) |
| C03 | Managed concierge | Customer delegates coordination of a multi-step service | brief → concierge → vendors/tasks → updates → outcome | [WeddingWire](https://www.weddingwire.com/) |
| C04 | Document review only | User submits material and receives expert review without full case handling | upload → review → comments/result | [LegalZoom](https://www.legalzoom.com/legal-services) |

## E — Education, coaching & session programs

| ID | Model | What it means | Typical flow | English reference examples |
| --- | --- | --- | --- | --- |
| E01 | Cohort / class enrollment | Many learners join scheduled classes | goal → class → cohort/date → enroll → attend | [ClassPass](https://classpass.com/fitness) |
| E02 | Recurring 1:1 lessons | Learner repeatedly books the same or similar tutor/coach | goal → tutor → trial → recurring sessions | [Preply](https://preply.com/) |
| E03 | Coaching plan + sessions | Assessment creates an ongoing plan with progress tracking | assessment → plan → sessions → progress | [BetterHelp](https://www.betterhelp.com/) |
| E04 | Expert review / async feedback | User submits work and receives expert feedback asynchronously | submit → expert review → feedback → revision | [Fiverr](https://www.fiverr.com/) |

## T — Remote & hybrid consultation

| ID | Model | What it means | Typical flow | English reference examples |
| --- | --- | --- | --- | --- |
| T01 | Remote consultation | Entire service interaction can happen remotely | need → expert → schedule/on-demand → video/chat | [Teladoc Health](https://www.teladochealth.com/), [BetterHelp](https://www.betterhelp.com/) |
| T02 | Hybrid remote + onsite | Remote triage or planning leads to physical service when needed | remote intake → decision → onsite/remote completion | [Teladoc Health](https://www.teladochealth.com/) |
| T03 | Async expert Q&A | User submits a question and receives a non-live professional answer | question → payment/triage → expert answer | — |

## L — Pickup, delivery & fulfillment

| ID | Model | What it means | Typical flow | English reference examples |
| --- | --- | --- | --- | --- |
| L01 | Pickup → process → return | Provider collects an item, performs service, then returns it | pickup → process → status → return | [Rinse](https://www.rinse.com/) |
| L02 | On-demand delivery fulfillment | Platform coordinates purchase/pickup and rapid delivery | basket/request → shopper/courier → track → deliver | [Instacart](https://www.instacart.com/), [DoorDash](https://www.doordash.com/) |
| L03 | Scheduled / recurring delivery | Delivery occurs on planned repeated dates | plan → schedule → recurring fulfillment | [Rinse](https://www.rinse.com/) |
| L04 | Business fulfillment / 3PL | Provider stores inventory and fulfills orders for businesses | inbound → storage → pick/pack → ship → returns | [ShipBob](https://www.shipbob.com/) |

## B — B2B managed-service models

| ID | Model | What it means | Typical flow | English reference examples |
| --- | --- | --- | --- | --- |
| B01 | Managed contract / SLA | Ongoing service governed by contract, assets, tickets, and SLA | contract → requests/maintenance → SLA → reporting | — |
| B02 | Staffing / talent augmentation | Client requests people rather than a one-off deliverable | role → candidates → contract → ongoing work | [Upwork](https://www.upwork.com/) |
| B03 | RFP / procurement workflow | Buyer publishes requirements and vendors submit proposals | RFP → proposals → evaluation → award → project | [Upwork](https://www.upwork.com/) |
| B04 | Managed fulfillment / operations | Provider operates a recurring business process for the client | onboarding → operations → exceptions → reporting | [ShipBob](https://www.shipbob.com/) |
| B05 | Multi-site enterprise service | One client manages service across many physical sites/assets | sites/assets → requests → dispatch → SLA/reporting | — |

## V — Aggregation, networks & multi-tenant models

| ID | Model | What it means | Typical flow | English reference examples |
| --- | --- | --- | --- | --- |
| V01 | Vertical aggregator / OTA | Platform aggregates inventory from many businesses in one vertical | search → compare → availability → transact | [Zocdoc](https://www.zocdoc.com/), [Fresha](https://www.fresha.com/) |
| V02 | Provider network | Customer accesses a network under common rules/coverage | eligibility → network → provider → service | [Care.com](https://www.care.com/) |
| V03 | Franchise / multi-tenant network | Similar businesses operate independently under shared product structure | tenant/location → catalog → booking/order | — |
| V04 | Marketplace + membership | Marketplace access or better economics depend on membership | join → marketplace → transact → benefits | [ClassPass](https://classpass.com/try), [Care.com](https://www.care.com/) |

## X — Hybrid commercial patterns

| ID | Model | What it means | Typical flow | English reference examples |
| --- | --- | --- | --- | --- |
| X01 | Service + commerce | Service and physical product purchase are one journey | product/service → compatibility → purchase/book → fulfill | [DoorDash](https://www.doordash.com/), [Instacart](https://www.instacart.com/) |
| X02 | Service + care plan | One-off interaction becomes a multi-session or longitudinal plan | assessment → plan → sessions → progress | [Teladoc Health](https://www.teladochealth.com/) |
| X03 | Family / manager dashboard | Someone manages service for another person or group | manager → member/case → schedule → updates | [Care.com](https://www.care.com/) |
| X04 | Event/vendor bundle | Multiple service providers are coordinated around one event | event brief → vendors/packages → schedule → event | [WeddingWire](https://www.weddingwire.com/) |
| X05 | Experience marketplace | Customer books a hosted activity rather than a conventional appointment | discover → host/experience → date → book | [Airbnb Experiences](https://www.airbnb.com/experiences) |

---

# How to select a project model

For a chosen product family, identify the smallest model combination that defines the real product. Avoid vague selections such as `marketplace` without specifying how matching, pricing, scheduling, and fulfillment work.

Examples:

```text
HOME-CLEANING + D03
= scheduled in-home cleaning company

HOME-CLEANING + M02 + S01
= managed cleaner marketplace with recurring subscriptions

PRO-LEGAL + A04 + C01
= consultation-first law firm with case/document tracking

EDU-TUTOR + M01 + E02
= tutor marketplace with recurring 1:1 lessons

AUTO-ROADSIDE + D02 + S03
= membership-based emergency roadside assistance

EVENT-VENUE + R01 + M01
= venue marketplace with date/time reservation
```

Phase 01 should receive the selected **family ID + model ID(s) + vertical variant**, not only a generic website idea.
