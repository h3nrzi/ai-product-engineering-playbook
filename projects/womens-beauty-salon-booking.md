# Project Tracker — Women’s Beauty Salon Booking

> Operational control panel for the project. Product behavior belongs in the PRD; this tracker only shows where the project is, what is authoritative, and what should happen next.

## 1. Project Snapshot

| Field | Value |
| --- | --- |
| Product family | Barbershop / Beauty Salon Booking ([catalog](../opportunities/service-products.md)) |
| Selected model / variant | **Women’s single-salon** |
| Target market / geography | Persian-language product for the Iranian market |
| Current playbook phase | **02 — Module-by-Module Engineering** |
| Current product delivery phase | **1 — Core Scheduling MVP** |
| Current module | **M01 — Identity & Access** |
| Overall status | **active** |
| PRD | [`womens-beauty-salon-booking/prd.md`](womens-beauty-salon-booking/prd.md) |
| Implementation repository | https://github.com/h3nrzi/beauty-salon |
| Documentation root | [`projects/womens-beauty-salon-booking/`](womens-beauty-salon-booking/) |

### Product boundary

- **Selected:** one physical women’s beauty salon where customers discover services/specialists and book appointments against salon-controlled availability, while salon staff manage the same operational schedule.
- **Explicitly not:** men’s barbershop, unisex salon, independent-specialist marketplace, multi-salon marketplace, multi-branch salon network, or beauty-at-home/mobile workforce product.

A deliberate model change must update the PRD and this tracker before work continues.

---

## 2. Playbook Progress

| Playbook Phase | Status | Exit Result |
| --- | --- | --- |
| 01 — Product Discovery & Delivery Plan | **complete** | Authoritative phased PRD + active-phase module map |
| 02 — Module-by-Module Engineering | **active** | Reviewed working modules / completed product delivery phases |
| 03 — Visual Redesign & UI Polish | not started | Final Stitch-driven visual redesign/polish when needed |

---

## 3. Product Delivery Roadmap

| Delivery Phase | Status | Outcome | Scope Summary |
| --- | --- | --- | --- |
| **1 — Core Scheduling MVP** | **active** | One salon can publish its bookable offering; customers can find and book valid appointments; staff can operate the shared schedule. | Identity/access, services and specialists, schedules/availability, public discovery, booking lifecycle, customer appointments, reception calendar and appointment operations. No online payment/refund integration yet. |
| **2 — Transactions & Reliability** | planned | Booking becomes financially and operationally robust enough for real deposit-based operation. | Deposit/payment flow, payment uncertainty, refunds, cancellation/rescheduling policy enforcement, salon-proposed changes, SMS/communication delivery and recovery, stronger operational edge cases. |
| **3 — Operations & Growth** | planned | The salon gains higher-leverage operational and growth capabilities after the core system is proven. | Advanced reporting/operational tooling, richer customer retention/growth capabilities, and additional improvements justified by actual use. Exact scope remains intentionally open. |

Future phases stay high-level until they become active.

### Active delivery phase

- **Phase:** 1 — Core Scheduling MVP
- **Objective:** Make the product genuinely usable by one salon for the complete non-payment appointment loop: configure offering and availability → customer discovers and books → customer can retrieve the booking → reception sees and manages the same appointment.
- **Exit condition:** A configured salon can operate a coherent end-to-end booking schedule with real customer/staff access boundaries, valid availability, persistent appointments, and consistent customer/reception views without relying on online payment or future-phase integrations.

---

## 4. Module Board — Delivery Phase 1

| ID | Module | Status | Depends On | Engineering Stage | Primary Artifact |
| --- | --- | --- | --- | --- | --- |
| **M01** | Identity & Access | **ready** | none | local `grill-with-docs` | pending local engineering output |
| **M02** | Salon Catalog & Specialists | planned | M01 | — | pending |
| **M03** | Scheduling & Availability | planned | M02 | — | pending |
| **M04** | Public Discovery | planned | M02 | — | pending |
| **M05** | Booking Lifecycle | planned | M01, M02, M03 | — | pending |
| **M06** | Customer Appointments | planned | M01, M05 | — | pending |
| **M07** | Salon Appointment Operations | planned | M01, M03, M05 | — | pending |

Module boundaries describe product responsibility, not folders or technical layers. Architecture for each module is decided only when that module enters Phase 02.

---

## 5. Current Focus

- **Current module:** M01 — Identity & Access
- **Current activity:** Local Codex / Matt methodology handoff
- **Immediate objective:** Clone/open the empty implementation repository locally and run M01 through `grill-with-docs` using the PRD as product authority.
- **Working artifact:** [`womens-beauty-salon-booking/prd.md`](womens-beauty-salon-booking/prd.md), especially M01 and identity/access sections

### Open decisions

| Decision | Owner | Needed For | Status |
| --- | --- | --- | --- |
| M01 technical architecture (auth/session/provider/authorization design) | Local Codex engineering interview + User | M01 implementation | open |
| M01 execution depth (`implement` directly vs `to-spec`/`to-tickets`) | Local Codex after grilling | M01 execution | open |

These are engineering decisions, not missing product-discovery decisions.

---

## 6. Risks & Blockers

| Type | Item | Impact | Resolution / Next Check |
| --- | --- | --- | --- |
| risk | Phase 1 could expand into payment/refund complexity | Would delay proving the core scheduling loop | Keep payment/refund in Delivery Phase 2 unless a real product contradiction appears |
| risk | Module boundaries may expose hidden coupling during engineering | Could require a small boundary adjustment | Refine internal architecture in Phase 02 without silently changing product ownership |

No current blocker. The implementation repository is linked and intentionally starts empty.

---

## 7. Authority & Artifacts

| Artifact | Role | Location |
| --- | --- | --- |
| PRD | **Product authority** | [`womens-beauty-salon-booking/prd.md`](womens-beauty-salon-booking/prd.md) |
| Active module artifact | Current engineering authority | Pending local M01 engineering output |
| Implementation repository | Source code and engineering evidence | https://github.com/h3nrzi/beauty-salon |
| Visual redesign artifact | UI authority if Phase 03 is used | Pending |
| Project workspace | Lightweight project context | [`womens-beauty-salon-booking/README.md`](womens-beauty-salon-booking/README.md) |

Do not duplicate PRD/module specs in this tracker.

---

## 8. Next Action

> **Run M01 — Identity & Access locally in `h3nrzi/beauty-salon` with Codex using `grill-with-docs`, and bring the architecture questions/decisions back for review when needed.**

The local engineering agent should inspect the repository and use the PRD as product authority. It should decide implementation architecture rather than rediscover the product.

---

## 9. Session Handoff

- **Where we are:** Playbook Phase 02; Delivery Phase 1 — Core Scheduling MVP; M01 — Identity & Access is the first ready module.
- **What is settled:** The product model, three-phase delivery roadmap, complete Phase 1 boundary, seven-module Phase 1 map, M01 product responsibility, and implementation repository are settled.
- **What is happening now:** M01 is ready for the local Codex/Matt methodology engineering interview in `h3nrzi/beauty-salon`.
- **What happens next:** Run `grill-with-docs` locally; resolve its architecture questions; then choose direct implementation or spec/tickets based on module size.

### Guide entrypoint

Read in this order:

1. [`MASTER.md`](../MASTER.md)
2. this tracker
3. [`phases/02-module-engineering.md`](../phases/02-module-engineering.md)
4. [`womens-beauty-salon-booking/prd.md`](womens-beauty-salon-booking/prd.md)
5. the active M01 engineering artifact / latest local Codex output once created

Continue from M01. Do not restart discovery or reopen the delivery roadmap without a real product contradiction.
