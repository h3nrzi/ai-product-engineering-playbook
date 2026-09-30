# Project Tracker — The Gentleman

## Project

- Product repository: https://github.com/h3nrzi/the-gentleman
- Product type: salon/service booking product with public content, customer booking/account journeys, and staff/admin workflows
- Workflow origin: initial Base44 vibe-coded frontend prototype, then structured frontend product definition and engineering with Codex and Matt Pocock-style skills
- Current workflow phase: **04 — Frontend Engineering**
- Current status: **in progress**

## Workflow status

| Phase | Status | Key artifact / evidence |
| --- | --- | --- |
| 01 — Product Discovery & Rapid Prototype | complete | Initial Base44 prototype brought into the product repository |
| 02 — Frontend Product Definition | complete | `.scratch/frontend-completion/map.md` and eight resolved decision tickets |
| 03 — Frontend Specification & Decomposition | complete | `.scratch/frontend-completion/spec.md`, acceptance/handoff artifacts, and approved 25-ticket implementation backlog |
| 04 — Frontend Engineering | in progress | `.scratch/frontend-completion-implementation/issues/` |
| 05 — Frontend Acceptance & Backend Handoff | not started as final phase | Partial acceptance evidence is collected ticket-by-ticket; final acceptance is Ticket 25 |
| 06 — Backend Product & Architecture Definition | not started | Backend must get a separate planning/Wayfinder phase after frontend completion |
| 07 — Backend Specification & Decomposition | not started | — |
| 08 — Backend Engineering | not started | — |
| 09 — Full-Stack Integration & Verification | not started | — |
| 10 — Production Hardening & Readiness | not started | — |

## Current frontend engineering progress

The approved implementation backlog contains 25 tickets.

Current known progress:

- Ticket 01 — contracts/browser foundation: **closed**
- Ticket 02 — guest booking/authoritative availability: **closed**
- Ticket 03 — booking review/recovery: **closed**
- Ticket 04 — uncertain booking creation/reconciliation: **implemented, ready-for-human**; automated criteria 04.1–04.5 are complete, while `04.Q` manual acceptance remains open
- Ticket 05 onward: not yet treated as complete in this tracker

Ticket 04 currently has partial manual evidence only. Full keyboard/focus, labels/states, mobile/Persian/RTL and screen-reader checks remain unperformed; real-device checks are blocked by unavailable devices.

## Current activity

Finish Ticket 04 human acceptance, then continue the frontend implementation frontier.

Ticket 04 covers stable create-attempt identity, safe replay, three-outcome reconciliation (`committed` / `not committed` / `unknown`), lost-response recovery, reload/persistence recovery, duplicate-submit prevention, and safe handling of unavailable/corrupt storage.

## Current artifacts

In the product repository:

- Frontend decision map: `.scratch/frontend-completion/map.md`
- Frontend specification: `.scratch/frontend-completion/spec.md`
- Acceptance matrix: `.scratch/frontend-completion/acceptance.md`
- Backend behavioral handoff: `.scratch/frontend-completion/backend-handoff.md`
- Implementation backlog: `.scratch/frontend-completion-implementation/backlog.md`
- Implementation tickets: `.scratch/frontend-completion-implementation/issues/`
- Per-ticket testing evidence: `docs/testing/`

Important current ticket:

- `.scratch/frontend-completion-implementation/issues/04-booking-attempt-reconciliation.md`

## Next action

Complete Ticket 04's outstanding manual acceptance (`04.Q`) and close it if the required human checks pass. Then inspect the backlog frontier and start the next eligible implementation ticket.

## Blockers / manual checks

For Ticket 04:

- complete keyboard-only recovery flow and visible/logical focus checks
- inspect labels, messages and recovery states manually
- inspect mobile layout/touch behavior
- inspect Persian/RTL presentation
- perform a screen-reader spot check
- real Android Chrome / iOS Safari checks remain blocked until devices are available unless an explicit accepted exception is recorded

## Backend transition rule

Do **not** start implementing the production backend immediately after frontend tickets finish.

After frontend acceptance, begin a separate backend definition phase. Preserve the settled product semantics and frontend-facing contracts, but independently decide production backend architecture, persistence, authentication/authorization, transactional boundaries, concurrency, idempotency, reconciliation, observability, infrastructure, and deployment.

Frontend mock behavior is evidence of intended semantics, not proof of production security, durability, atomicity, or distributed concurrency guarantees.

## Guide LLM entrypoint

When starting a new guidance session for The Gentleman:

1. Read [`../MASTER.md`](../MASTER.md).
2. Read this tracker.
3. Read the active phase guide under [`../phases/`](../phases/README.md) once it exists.
4. Inspect the product repository and current ticket/evidence before making status claims.
5. Help the user understand the current work, review agent output, make decisions, and formulate concise prompts/responses.
6. Do not implement application code yourself unless the user explicitly asks for a small illustrative example.
