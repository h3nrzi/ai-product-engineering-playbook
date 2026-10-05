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

A model change requires explicit user authorization for a product revision. The approved PRD remains read-only during engineering; live progress belongs here.

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
| **M01** | Identity & Access | **active** | none | spec published; `to-tickets` next | [M01 spec](https://github.com/h3nrzi/beauty-salon/blob/d074f8a21649cb50c6bd9fa2084e484cb1862919/.scratch/m01-identity-access/spec.md) |
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
- **Current activity:** Ticket decomposition after the completed interview and published spec
- **Immediate objective:** Run `to-tickets` against the existing spec, preserve accepted decisions, and review the vertical slices and blocking edges.
- **Working artifact:** [M01 spec](https://github.com/h3nrzi/beauty-salon/blob/d074f8a21649cb50c6bd9fa2084e484cb1862919/.scratch/m01-identity-access/spec.md)

### Open decisions

No open M01 design decisions are recorded in the published spec. Ticket granularity and dependencies still need review. Hosting and live SMS credentials/template remain operational prerequisites, not a reason to reopen product discovery.

---

## 6. Risks & Blockers

| Type | Item | Impact | Resolution / Next Check |
| --- | --- | --- | --- |
| risk | Phase 1 could expand into payment/refund complexity | Would delay proving the core scheduling loop | Keep payment/refund in Delivery Phase 2 unless a real product contradiction appears |
| risk | Module boundaries may expose hidden coupling during engineering | Could require a small boundary adjustment | Refine internal architecture in Phase 02 without silently changing product ownership |

Automated implementation can proceed using the controlled test delivery substitute. Hosting selection and live SMS credentials/template remain operational prerequisites; M01 acceptance requires the live Kavenegar verification described in the spec. No implementation or acceptance is claimed.

---

## 7. Authority & Artifacts

| Artifact | Role | Location |
| --- | --- | --- |
| PRD | **Product authority** | [`womens-beauty-salon-booking/prd.md`](womens-beauty-salon-booking/prd.md) |
| Active module artifact | Current engineering authority | [M01 spec](https://github.com/h3nrzi/beauty-salon/blob/d074f8a21649cb50c6bd9fa2084e484cb1862919/.scratch/m01-identity-access/spec.md) |
| Implementation repository | Source code and engineering evidence | https://github.com/h3nrzi/beauty-salon |
| Visual redesign artifact | UI authority if Phase 03 is used | Pending |
| Project workspace | Lightweight project context | [`womens-beauty-salon-booking/README.md`](womens-beauty-salon-booking/README.md) |

Do not duplicate PRD/module specs in this tracker.

---

## 8. Next Action

> **Run `to-tickets` on the existing M01 spec in `h3nrzi/beauty-salon`, then review the proposed vertical slices and dependencies before publishing tickets.**

## 9. Session Handoff

- **Where we are:** Playbook Phase 02; Delivery Phase 1; M01 specification published.
- **What is settled:** Product baseline, completed engineering interview, accepted ADRs, and behavioral test boundary are recorded in the implementation repository.
- **What is happening now:** Ticket decomposition is next; no ticket files or implementation were present in the reviewed commit.
- **What happens next:** Approve and publish the ticket graph, then implement and review. Keep acceptance open until all required evidence, including live SMS verification, exists.
- **Evidence reviewed:** Implementation repository commit `d074f8a21649cb50c6bd9fa2084e484cb1862919` on 2026-10-05. These are tracker updates, not changes to the approved PRD.

### Guide entrypoint

Read in this order:

1. [`MASTER.md`](../MASTER.md)
2. this tracker
3. [`phases/02-module-engineering.md`](../phases/02-module-engineering.md)
4. [`womens-beauty-salon-booking/prd.md`](womens-beauty-salon-booking/prd.md)
5. the active M01 engineering artifact / latest local Codex output once created

Continue from M01. Do not restart discovery or reopen the delivery roadmap without a real product contradiction.
