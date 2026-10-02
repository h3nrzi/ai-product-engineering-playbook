# Project Tracker — The Gentleman

## Project

- Product repository: https://github.com/h3nrzi/the-gentleman
- Product type: service/salon booking product with public content, customer journeys, and staff/admin workflows
- Origin: Base44 vibe-coded prototype, then structured frontend completion with Codex and Matt Pocock-style skills
- Current workflow phase: **04 — Frontend Engineering**
- Current status: **in progress**
- Long-term implementation direction: **integrated full-stack Next.js**
- Separate dedicated NestJS/Express backend: **not currently planned**

## Workflow status

```text
Phase 01 — Product Discovery / Prototype        COMPLETE
Phase 02 — Wayfinder / Product Definition       COMPLETE
Phase 03 — to-spec + to-tickets                 COMPLETE
Phase 04 — Implement frontend tickets           IN PROGRESS
```

The current playbook ends at **Frontend Accepted**. Later full-stack/server-side work will be designed just in time when this project is deliberately selected to continue beyond Phase 04.

## Frontend engineering

The approved implementation backlog contains 25 tickets under:

`.scratch/frontend-completion-implementation/issues/`

Tickets **01–07 have been implemented/closed in the product repository**. The user has continued sequential ticket execution beyond that point; when exact current-ticket status matters, inspect the product repository rather than relying on this tracker alone.

The normal activity is intentionally simple:

```text
Pick next ready ticket
→ implement with Codex/engineering agent
→ verify relevant behavior
→ close/accept
→ next ticket
```

Do not add planning ceremony between tickets unless a real spec/decision gap or blocker appears.

## Important artifacts

In the product repository:

- Decision map: `.scratch/frontend-completion/map.md`
- Frontend specification: `.scratch/frontend-completion/spec.md`
- Acceptance material: `.scratch/frontend-completion/acceptance.md`
- Existing server/backend behavioral notes: `.scratch/frontend-completion/backend-handoff.md`
- Implementation backlog: `.scratch/frontend-completion-implementation/backlog.md`
- Implementation tickets: `.scratch/frontend-completion-implementation/issues/`

These existing artifacts remain useful historical/behavioral context. They do **not** imply that a separate backend application must be built.

## Current implementation strategy

The user has decided that The Gentleman should ultimately become a **full-stack Next.js application** rather than a frontend plus a separately developed dedicated backend.

For future work, think in terms of one product containing the appropriate client and server boundaries:

```text
Next.js
├── public site
├── customer area
├── staff/admin area
├── server-side/domain behavior
├── auth/authz
└── persistence/database
```

This does not remove engineering boundaries. Real server-side work will still need to handle authorization, validation, persistence, concurrency-sensitive scheduling, atomic mutations, revisions/idempotency/reconciliation, and other guarantees currently modeled by frontend mocks.

Do not prematurely choose the exact database/auth/ORM/infrastructure mechanisms during Phase 04.

## Future transition rule

Do **not** automatically start a separate backend after Ticket 25.

First reach **Frontend Accepted**. When the user explicitly chooses to continue The Gentleman, use it to design the next playbook phase just in time.

That future phase should be framed around making the product genuinely full-stack/server-backed—likely inside Next.js under the current strategy—rather than assuming a NestJS/Express service.

Preserve established product semantics and useful frontend-facing contracts while replacing mock/demo guarantees with real server-side guarantees.

## Guide LLM entrypoint

When starting a new guidance session for The Gentleman:

1. Read `../MASTER.md`.
2. Read this tracker.
3. Read the active phase guide as needed.
4. Inspect the product repository/current ticket before making exact progress claims.
5. Keep guidance proportional: after discovery, the normal frontend-completion path is Wayfinder → to-spec → to-tickets → ticket implementation.
6. Help with real decisions, blockers, reviews, and concise agent responses; do not manufacture extra process.
7. Do not implement application code yourself unless explicitly asked for a small illustrative example.
