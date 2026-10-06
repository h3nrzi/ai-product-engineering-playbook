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
| **M01** | Identity & Access | **active — final acceptance pending** | none | Implementation and tickets 01–06 complete; ticket 07 `ready-for-human` / incomplete | [M01 spec](https://github.com/h3nrzi/beauty-salon/blob/281a9c4d8283cc1d01a56eece62bdfebd7c04f3e/.scratch/m01-identity-access/spec.md); [Ticket 07 — acceptance matrix and remaining checks](https://github.com/h3nrzi/beauty-salon/blob/281a9c4d8283cc1d01a56eece62bdfebd7c04f3e/.scratch/m01-identity-access/issues/07-self-hosted-m01-acceptance.md) |
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
- **Current activity:** Final self-hosted acceptance; implementation, ticket decomposition and tickets 01–06 are complete.
- **Immediate objective:** Complete ticket 07's four outstanding deployment/live acceptance items on the intended host. M01 remains active until this evidence exists.
- **Working artifacts:** [M01 tickets](https://github.com/h3nrzi/beauty-salon/tree/281a9c4d8283cc1d01a56eece62bdfebd7c04f3e/.scratch/m01-identity-access/issues); [Ticket 07 — acceptance matrix and remaining checks](https://github.com/h3nrzi/beauty-salon/blob/281a9c4d8283cc1d01a56eece62bdfebd7c04f3e/.scratch/m01-identity-access/issues/07-self-hosted-m01-acceptance.md); [Deployment runbook](https://github.com/h3nrzi/beauty-salon/blob/281a9c4d8283cc1d01a56eece62bdfebd7c04f3e/deployment/README.md)
- **Recorded validation:** Ticket 07's local assembled run passed typecheck, 60 integration/provider/configuration tests against real PostgreSQL, seven Chromium journeys and the production build. Local restricted-runtime checks and application restart persistence passed. Final Standards/Spec review recorded zero actionable findings; these results do not establish intended-host acceptance.
- **Live SMS evidence:** [Ticket 06 — live Kavenegar evidence](https://github.com/h3nrzi/beauty-salon/blob/281a9c4d8283cc1d01a56eece62bdfebd7c04f3e/.scratch/m01-identity-access/issues/06-kavenegar-sign-in.md) records user-confirmed Kavenegar receipt and customer `/customer` verification, plus manager `/staff` access, on `localhost:3000` on 2026-10-06. The agent did not independently perform those live journeys. Ticket 06 is complete; local evidence does not prove connectivity or live verification from the intended host.

### Open decisions

No open M01 product/design decisions are recorded. Hosting/domain/access, certificate provisioning and intended-host/network verification remain operational prerequisites. The prior live Kavenegar credentials/template/recipient block is resolved for the local check; provision and verify the intended deployment using the existing runbook without reopening discovery or repeating `to-tickets`.

---

## 6. Risks & Blockers

| Type | Item | Impact | Resolution / Next Check |
| --- | --- | --- | --- |
| blocker — operational acceptance | Intended self-hosted host/domain/access and persistent PostgreSQL deployment are not yet verified | Ticket 07 and final M01 acceptance remain incomplete | Provision the intended environment; follow the deployment runbook and verify persistence after application/container replacement |
| blocker — operational acceptance | HTTPS, reverse-proxy trust boundary, secure cookies and forwarded-header protection on the intended host remain unverified | Local checks cannot establish secure deployed authentication or IP-limit enforcement | Configure certificate/proxy and verify the deployed trust boundary and cookie behavior |
| blocker — operational acceptance | Iranian-network reachability, intended-host connectivity to Kavenegar and deployed real customer/staff verification remain outstanding | Local live Kavenegar evidence does not complete assembled deployment acceptance | Verify access from an Iranian network and outbound provider connectivity; complete real-code customer/staff journeys on the intended deployment and confirm production rejects test delivery |
| blocker — environment | Docker runtime image build failed with BuildKit metadata I/O error; host had about 116 MiB free | Container image build, nginx/certificate execution and Compose volume persistence remain unverified | Free sufficient host/Docker storage and rerun the container exercise; record as an environment failure, not an application defect or passing build |
| risk | Phase 1 could expand into payment/refund complexity | Would delay proving the core scheduling loop | Keep payment/refund in Delivery Phase 2 unless a real product contradiction appears |
| risk | Module boundaries may expose hidden coupling during engineering | Could require a small boundary adjustment | Refine internal architecture in Phase 02 without silently changing product ownership |

Implementation and local/integration acceptance evidence are recorded in [Ticket 07 — acceptance matrix and remaining checks](https://github.com/h3nrzi/beauty-salon/blob/281a9c4d8283cc1d01a56eece62bdfebd7c04f3e/.scratch/m01-identity-access/issues/07-self-hosted-m01-acceptance.md). Live local Kavenegar verification is recorded in [Ticket 06 — live Kavenegar evidence](https://github.com/h3nrzi/beauty-salon/blob/281a9c4d8283cc1d01a56eece62bdfebd7c04f3e/.scratch/m01-identity-access/issues/06-kavenegar-sign-in.md). Ticket 07 remains `ready-for-human` and **incomplete**; review and local passes do not close the four deployment/live items.

---

## 7. Authority & Artifacts

| Artifact | Role | Location |
| --- | --- | --- |
| PRD | **Product authority** | [`womens-beauty-salon-booking/prd.md`](womens-beauty-salon-booking/prd.md) |
| Active module artifact | Current engineering authority | [M01 spec](https://github.com/h3nrzi/beauty-salon/blob/281a9c4d8283cc1d01a56eece62bdfebd7c04f3e/.scratch/m01-identity-access/spec.md) |
| Module tickets | Completed slices and remaining acceptance | [M01 tickets](https://github.com/h3nrzi/beauty-salon/tree/281a9c4d8283cc1d01a56eece62bdfebd7c04f3e/.scratch/m01-identity-access/issues) |
| Live provider evidence | User-confirmed local Kavenegar acceptance | [Ticket 06 — live Kavenegar evidence](https://github.com/h3nrzi/beauty-salon/blob/281a9c4d8283cc1d01a56eece62bdfebd7c04f3e/.scratch/m01-identity-access/issues/06-kavenegar-sign-in.md) |
| Final module acceptance | Local validation matrix and outstanding deployment checks | [Ticket 07 — acceptance matrix and remaining checks](https://github.com/h3nrzi/beauty-salon/blob/281a9c4d8283cc1d01a56eece62bdfebd7c04f3e/.scratch/m01-identity-access/issues/07-self-hosted-m01-acceptance.md) |
| Deployment instructions | Intended-host acceptance procedure | [Deployment runbook](https://github.com/h3nrzi/beauty-salon/blob/281a9c4d8283cc1d01a56eece62bdfebd7c04f3e/deployment/README.md) |
| Implementation repository | Source code and engineering evidence | https://github.com/h3nrzi/beauty-salon |
| Reviewed evidence commit | Fixed implementation/evidence snapshot, reviewed 2026-10-06 | [`281a9c4d8283cc1d01a56eece62bdfebd7c04f3e`](https://github.com/h3nrzi/beauty-salon/commit/281a9c4d8283cc1d01a56eece62bdfebd7c04f3e) |
| Visual redesign artifact | UI authority if Phase 03 is used | Pending |
| Project workspace | Lightweight project context | [`womens-beauty-salon-booking/README.md`](womens-beauty-salon-booking/README.md) |

Do not duplicate PRD/module specs in this tracker.

---

## 8. Next Action

> **Complete ticket 07's intended-host acceptance using the deployment runbook: resolve the host/storage prerequisites, verify persistent deployment, HTTPS/proxy and secure cookies, Iranian-network access and Kavenegar connectivity, then real customer/staff sign-in. Record the results before marking ticket 07 and M01 complete; next select M02 — Salon Catalog & Specialists.**

---

## 9. Session Handoff

- **Where we are:** Playbook Phase 02; Delivery Phase 1; M01 implementation complete, final self-hosted acceptance pending.
- **What is settled:** Approved product baseline, M01 interview/spec/ADRs and ticket graph; tickets 01–06 have complete acceptance checklists, including user-confirmed local live Kavenegar customer verification and manager staff access. Ticket 07's deployment artifacts and local assembled verification are recorded.
- **What is happening now:** Ticket 07 is `ready-for-human` / incomplete. Intended host/persistent deployment, HTTPS/proxy/cookies, Iranian-network/provider connectivity and deployed real-code journeys remain outstanding. Docker image build hit a storage environment failure (about 116 MiB free); container/proxy/volume acceptance remains unverified.
- **What happens next:** Resolve operational prerequisites and complete the four remaining ticket 07 items. Reuse valid existing evidence and repeat checks affected by deployment. Only then mark M01 complete and select M02 — Salon Catalog & Specialists; do not repeat discovery, specification or ticket decomposition.
- **Evidence reviewed:** Implementation repository commit [`281a9c4d8283cc1d01a56eece62bdfebd7c04f3e`](https://github.com/h3nrzi/beauty-salon/commit/281a9c4d8283cc1d01a56eece62bdfebd7c04f3e) on 2026-10-06. Ticket 07 records passing typecheck, 60 integration/provider/configuration tests, seven Chromium journeys, production build and final review with zero actionable findings. The approved PRD and parent M01 specification are unchanged.

### Guide entrypoint

Read in this order:

1. [`MASTER.md`](../MASTER.md)
2. this tracker
3. [`phases/02-module-engineering.md`](../phases/02-module-engineering.md)
4. [`womens-beauty-salon-booking/prd.md`](womens-beauty-salon-booking/prd.md)
5. the pinned M01 spec, tickets 06/07 evidence and deployment runbook linked above

Continue from M01. Do not restart discovery or reopen the delivery roadmap without a real product contradiction.
