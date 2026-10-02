# Phase 04 — React to Next.js Refactor with Matt Methodology

## Goal

Refactor the completed React frontend into a clean Next.js application without using the migration as an excuse to redesign the product.

The React app entering this phase is the behavioral reference. The objective is framework migration and preparation for full-stack implementation while preserving accepted product behavior.

## Operational workflow

Use the same lightweight Matt-style pattern:

```text
Completed React frontend
→ Wayfinder / migration analysis
→ resolve migration decisions
→ to-spec
→ approve migration spec
→ to-tickets
→ approve tickets
→ implement migration tickets
→ parity / quality verification
→ Next.js frontend ready
```

## Key concerns

The migration should deliberately decide only what is needed for a sound Next.js foundation, such as routing/layout boundaries, client/server component boundaries where relevant, data-access boundaries, browser-only assumptions, metadata/assets, and how existing frontend contracts/mocks survive the migration.

Do not prematurely implement the final database/auth/backend merely because Next.js supports server-side code. That belongs to Phase 05.

## Guide LLM role

Help analyze agent questions and migration tradeoffs, protect behavioral parity, prevent unnecessary rewrites, and keep the migration ticketed and reviewable. Do not write the application code.

## Exit criteria

Phase 04 is complete when the accepted React experience has been migrated to Next.js with the important journeys preserved, relevant checks passing, and a clean enough server/client boundary to begin full-stack completion.

Then proceed to **Phase 05 — Full-Stack Next.js Completion**.
