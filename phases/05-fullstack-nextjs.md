# Phase 05 — Full-Stack Next.js Completion

## Goal

Turn the migrated Next.js frontend into the real full-stack product by replacing prototype/mock boundaries with production-oriented server-side behavior and persistence.

This is the final phase of the current workflow.

## Direction

The default architecture for this portfolio is an integrated full-stack Next.js product. A separate NestJS/Express backend is not assumed. Use a separate service only when a real project requirement explicitly justifies it.

## Operational workflow

The exact server-side decisions depend on the real project, so use the same structured pattern rather than pre-inventing a universal backend architecture:

```text
Next.js frontend ready
→ Wayfinder / full-stack analysis
→ resolve server-side/product guarantees
→ to-spec
→ approve full-stack spec
→ to-tickets
→ approve tickets
→ implement tickets
→ integrated verification
→ full-stack product complete
```

## What this phase must replace

Where relevant to the product, replace demo/mock behavior with real implementations for concerns such as persistence, authentication/session handling, authorization, validation, authoritative business rules, transactional/atomic mutations, concurrency-sensitive operations, idempotency/reconciliation, file/external integrations, and operational error handling.

The frontend behavior established earlier should not be casually redesigned during this work. Server implementation should provide real guarantees behind the established product semantics.

## Architecture discipline

Do not put all server logic directly into UI components merely because Next.js allows server code in the same repository. Preserve meaningful domain/application/data boundaries appropriate to the project.

Do not add distributed services, queues, caches, object storage, or other infrastructure unless the product actually needs them.

## Guide LLM role

Help the user analyze Wayfinder questions, make architecture/product-boundary decisions, review specs/tickets, and evaluate implementation evidence. The Guide remains advisory; engineering agents implement.

## Exit criteria

The phase is complete when the important product journeys use real server-backed behavior, required security/authorization and business guarantees exist, persistence/integrations are real where required, integrated verification is satisfactory, and the product can honestly be described as a completed full-stack Next.js application for its defined scope.
