# Project Tracker — Women’s Beauty Salon Booking

> Operational control panel for the project. Product behavior belongs in the PRD; this tracker only shows where the project is, what is authoritative, and what should happen next.

## 1. Project Snapshot

| Field | Value |
| --- | --- |
| Product family | Barbershop / Beauty Salon Booking ([catalog](../opportunities/service-products.md)) |
| Selected model / variant | **Women’s single-salon** |
| Target market / geography | Persian-language product for the Iranian market |
| Current playbook phase | **01 — Product Discovery & Delivery Plan** |
| Current product delivery phase | **1 — Core Scheduling MVP** |
| Current module | None — module engineering has not started |
| Overall status | **active** |
| PRD | Pending — [`womens-beauty-salon-booking/prd.md`](womens-beauty-salon-booking/prd.md) |
| Implementation repository | Pending |
| Documentation root | [`projects/womens-beauty-salon-booking/`](womens-beauty-salon-booking/) |

### Product boundary

- **Selected:** one physical women’s beauty salon where customers discover services/specialists and book appointments against salon-controlled availability, while salon staff manage the same operational schedule.
- **Explicitly not:** men’s barbershop, unisex salon, independent-specialist marketplace, multi-salon marketplace, multi-branch salon network, or beauty-at-home/mobile workforce product.

A deliberate model change must update the PRD and this tracker before work continues.

---

## 2. Playbook Progress

| Playbook Phase | Status | Exit Result |
| --- | --- | --- |
| 01 — Product Discovery & Delivery Plan | **active** | Authoritative phased PRD + active-phase module map |
| 02 — Module-by-Module Engineering | not started | Reviewed working modules / completed product delivery phases |
| 03 — Visual Redesign & UI Polish | not started | Final Stitch-driven visual redesign/polish when needed |

---

## 3. Product Delivery Roadmap

| Delivery Phase | Status | Outcome | Scope Summary |
| --- | --- | --- | --- |
| **1 — Core Scheduling MVP** | **active planning** | One salon can publish its bookable offering; customers can find and book valid appointments; staff can operate the shared schedule. | Identity/access, services and specialists, schedules/availability, public discovery, booking lifecycle, customer appointments, reception calendar and appointment operations. No online payment/refund integration yet. |
| **2 — Transactions & Reliability** | planned | Booking becomes financially and operationally robust enough for real deposit-based operation. | Deposit/payment flow, payment uncertainty, refunds, cancellation/rescheduling policy enforcement, salon-proposed changes, SMS/communication delivery and recovery, stronger operational edge cases. |
| **3 — Operations & Growth** | planned | The salon gains higher-leverage operational and growth capabilities after the core system is proven. | Advanced reporting/operational tooling, richer customer retention/growth capabilities, and additional improvements justified by actual use. Exact scope remains intentionally open. |

Future phases stay high-level until they become active.

### Active delivery phase

- **Phase:** 1 — Core Scheduling MVP
- **Objective:** Make the product genuinely usable by one salon for the complete non-payment appointment loop: configure offering and availability → customer discovers and books → customer can retrieve the booking → reception sees and manages the same appointment.
- **Exit condition:** A configured salon can operate a coherent end-to-end booking schedule with real customer/staff access boundaries, valid availability, persistent appointments, and consistent customer/reception views without relying on online payment or future-phase integrations.

### Explicit Phase 1 deferrals

Phase 1 does **not** require:

- online deposit/payment gateway;
- refund processing;
- payment uncertainty/reconciliation;
- automated SMS delivery beyond any minimal authentication mechanism chosen during engineering;
- advanced cancellation/rescheduling financial policy;
- loyalty, wallet, packages, chat, CRM, accounting/POS, inventory, payroll, marketplace, multi-branch, or at-home service behavior;
- advanced analytics/growth tooling.

These deferrals prevent transactional integrations from blocking validation of the core scheduling product.

---

## 4. Module Board — Delivery Phase 1

| ID | Module | Status | Depends On | Engineering Stage | Primary Artifact |
| --- | --- | --- | --- | --- | --- |
| **M01** | Identity & Access | **ready** | none | — | pending |
| **M02** | Salon Catalog & Specialists | planned | M01 | — | pending |
| **M03** | Scheduling & Availability | planned | M02 | — | pending |
| **M04** | Public Discovery | planned | M02 | — | pending |
| **M05** | Booking Lifecycle | planned | M01, M02, M03 | — | pending |
| **M06** | Customer Appointments | planned | M01, M05 | — | pending |
| **M07** | Salon Appointment Operations | planned | M01, M03, M05 | — | pending |

### Module intent

**M01 — Identity & Access**  
Own customer authentication, staff authentication, session identity, and salon role/access boundaries. It should establish who is acting without deciding unrelated booking behavior.

**M02 — Salon Catalog & Specialists**  
Own services, specialists, service-to-specialist eligibility, and the manager-facing configuration required to make the salon’s offering publishable/bookable.

**M03 — Scheduling & Availability**  
Own specialist working schedules and computation of valid bookable availability. It is the shared source of scheduling truth used by customer booking and salon operations.

**M04 — Public Discovery**  
Own the public customer experience for understanding the salon, services, specialists, and entry into booking. It consumes catalog data but does not own salon configuration.

**M05 — Booking Lifecycle**  
Own creation of a valid appointment from selected service/specialist/time, conflict protection, booking state, and the customer-facing booking completion path for Phase 1. No online payment responsibility yet.

**M06 — Customer Appointments**  
Own authenticated customer retrieval of their appointments and Phase-1-safe appointment actions. It does not own staff operations or future payment/refund behavior.

**M07 — Salon Appointment Operations**  
Own the shared reception/manager calendar, appointment detail, staff-created appointments where included by the PRD, and operational status updates permitted in Phase 1.

### Dependency principle

Module boundaries describe product responsibility, not folders or technical layers. Architecture for each module is decided only when that module enters Phase 02.

---

## 5. Current Focus

- **Current module:** None
- **Current activity:** PRD synthesis
- **Immediate objective:** Turn the agreed three-phase roadmap and Phase 1 module map into the authoritative PRD
- **Working artifact:** `projects/womens-beauty-salon-booking/prd.md` (to be created)

### Open decisions

None currently blocking PRD drafting.

Detailed architecture decisions for M01 are intentionally deferred to its Phase 02 `grill-with-docs` session.

---

## 6. Risks & Blockers

| Type | Item | Impact | Resolution / Next Check |
| --- | --- | --- | --- |
| risk | Phase 1 could expand into payment/refund complexity | Would delay proving the core scheduling loop | Keep payment/refund in Delivery Phase 2 unless the PRD exposes a product contradiction |
| risk | Module boundaries may expose hidden coupling during engineering | Could require a small boundary adjustment | Allow Phase 02 to refine internal architecture without changing product ownership silently |

---

## 7. Authority & Artifacts

| Artifact | Role | Location |
| --- | --- | --- |
| PRD | Product authority | Pending — `projects/womens-beauty-salon-booking/prd.md` |
| Active module artifact | Current engineering authority | Not applicable until Phase 02 |
| Implementation repository | Source code and engineering evidence | Pending |
| Visual redesign artifact | UI authority if Phase 03 is used | Pending |
| Project workspace | Minimal project context | [`womens-beauty-salon-booking/README.md`](womens-beauty-salon-booking/README.md) |

---

## 8. Next Action

> **Write and approve the authoritative PRD using this delivery roadmap and Phase 1 module map.**

The PRD should define product behavior and acceptance outcomes clearly enough that **M01 — Identity & Access** can enter Phase 02 without rediscovering what product is being built.

---

## 9. Session Handoff

- **Where we are:** Playbook Phase 01; Product Delivery Phase 1 has been defined and decomposed into seven modules.
- **What is settled:** The product is a Persian women’s single-salon booking product. Delivery uses three phases. Phase 1 proves the full non-payment scheduling loop and defers online payments/refunds and advanced operational/growth capabilities.
- **What is happening now:** Converting the agreed product roadmap/module map into the authoritative PRD.
- **What happens next:** Draft and approve `projects/womens-beauty-salon-booking/prd.md`; then start Phase 02 with M01 — Identity & Access.

### Guide entrypoint

Read in this order:

1. [`MASTER.md`](../MASTER.md)
2. this tracker
3. [`phases/01-product-discovery.md`](../phases/01-product-discovery.md)
4. the PRD once created
5. the active module artifact / latest engineering output once Phase 02 starts

Continue from PRD synthesis. Do not reopen the delivery roadmap or module map without a real product contradiction.