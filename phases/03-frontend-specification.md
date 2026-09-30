# Phase 03 — Frontend Specification & Decomposition

## Purpose

Transform the approved product decisions from Phase 02 into a coherent, implementation-ready frontend specification, then decompose the approved specification into traceable implementation tickets.

This phase is **planning and compilation, not implementation**.

> **Phase 03 is compilation, not invention.**

The Guide LLM defined in [`../MASTER.md`](../MASTER.md) reviews the outputs of specification and decomposition agents, protects decision fidelity, and helps the user decide whether to approve, revise, or return upstream. It does not implement the frontend itself.

---

## Phase boundary

```text
PHASE 02 — RESOLVED DECISIONS
        ↓
      to-spec
        ↓
CANDIDATE FRONTEND SPEC
        ↓
SPEC QUALITY REVIEW
        ↓
USER APPROVAL
        ↓
     to-tickets
        ↓
CANDIDATE TICKET BREAKDOWN
        ↓
DECOMPOSITION REVIEW
        ↓
USER APPROVAL
        ↓
TRACEABILITY + HANDOFF
        ↓
PHASE 04 — FRONTEND ENGINEERING
```

There is a human approval gate between specification and decomposition, and another before implementation begins.

Do not silently run:

```text
to-spec → to-tickets → implement
```

as one uninterrupted operation.

---

## 1. Entry criteria

Phase 03 begins when Phase 02 is ready for specification.

Expected inputs include:

- the runnable/inspectable prototype and repository
- Prototype Handoff
- resolved decision map
- approved decision artifacts
- stable product vocabulary
- explicit deferrals
- recorded backend responsibility notes
- Phase 02 consistency/readiness review

The implementation tickets do not yet exist, and application implementation must not begin during this phase.

---

## 2. Responsibility boundary

Phase 02 answers:

> What should the product do and mean?

Phase 03 answers:

> How do we faithfully express those decisions as an implementation-ready frontend specification and executable engineering plan?

A product decision may say that a customer can reschedule only date/time while preserving specialist, services, and price snapshot. Phase 03 should make those semantics precise enough to implement and verify.

It should not unnecessarily prescribe details such as a particular HTTP route, state library, component pattern, persistence mechanism, or backend architecture unless a previously approved constraint genuinely requires that choice.

The specification should constrain **observable product behavior and required frontend-facing semantics** while leaving reasonable implementation freedom.

---

# Part I — Specification

## 3. Run specification only from approved decisions

The specification agent should treat Phase 02 artifacts as authoritative inputs.

Its job is to:

- consolidate approved decisions
- preserve their boundaries and semantics
- normalize terminology
- make behavior explicit enough for implementation
- preserve approved deferrals
- preserve frontend/mock versus production-backend responsibility boundaries
- expose traceable requirements

It must not reopen product discovery casually or introduce product behavior merely because it seems useful.

---

## 4. Spec Quality Protocol

After `to-spec`, stop for Guide and user review.

```text
Phase 02 Decisions
        ↓
      to-spec
        ↓
   Candidate Spec
        ↓
   Guide Review
        ↓
 ┌──────┼────────────┐
 ▼      ▼            ▼
PASS   SPEC FIX   DECISION GAP
 │      │            │
 │      └→ revise    ↓
 │                 Phase 02
 └────────────────→ APPROVE
```

### 4.1 Source fidelity

For each important requirement, ask:

> Where did this requirement come from?

It should be traceable to an approved source such as:

- an approved product decision
- explicit scope
- a known constraint
- an approved deferral/boundary

A plausible new behavior is still a new requirement if the user never approved it.

Do not allow specification generation to silently promote recommendations, assumptions, or implementation convenience into product requirements.

### 4.2 Semantic completeness

A specification can be technically consistent with a decision while losing essential semantics.

If an approved decision includes several meaningful guarantees or preserved values, the spec must retain them rather than collapsing them into a vague sentence.

When the decision already exists but its meaning was incompletely transferred, this is a **spec gap**, not a reason to reopen product definition.

### 4.3 Distinguish spec gaps from decision gaps

This distinction is mandatory.

#### Spec gap

```text
Approved decision exists
        ↓
Spec omitted/distorted it
        ↓
Revise spec
```

#### Decision gap

```text
Important behavior has no approved answer
        ↓
Spec would need to guess
        ↓
STOP
        ↓
Return to the relevant Phase 02 decision
```

Do not let the spec agent solve a missing product decision on its own.

### 4.4 Internal consistency

Review the specification as one system, not only section by section.

Look for:

- contradictions between requirements
- a general rule accidentally overriding an approved exception
- inconsistent state semantics
- incompatible scope statements
- different requirements describing the same concept differently

If the source decisions themselves conflict, return only the relevant decision area to Phase 02. If the decisions are sound and the spec introduced the conflict, revise the spec.

### 4.5 Domain vocabulary

Use the stable vocabulary established in Phase 02.

Avoid terminology drift where multiple names accidentally describe the same concept, such as switching unpredictably between customer/client/user or appointment/booking/reservation.

If two terms represent genuinely different concepts, the specification must make that distinction clear.

Terminology chosen here will propagate into UI, contracts, tests, tickets, and eventually backend work, so ambiguity should not be allowed to spread.

### 4.6 State and failure semantics

For important workflows, ensure the specification preserves the meaningful states and recovery semantics approved in Phase 02.

Depending on the workflow, these may include:

- validation/readiness
- loading or pending
- success
- known failure
- empty result
- stale/conflict state
- retry
- uncertain outcome
- reconciliation/recovery
- ownership/access behavior

Do not manufacture edge cases merely to make the specification appear comprehensive. Include states because they are meaningful to the approved product behavior.

### 4.7 Mock versus production boundary

The specification must preserve the difference between behavior demonstrated by the frontend/mock adapter and guarantees required from the future production backend.

For example:

```text
Mock responsibility
→ simulate the agreed atomic-booking semantics

Future backend responsibility
→ actually guarantee atomic reservation under concurrency
```

Do not describe mock evidence as proof of production security, authorization, concurrency, durability, or infrastructure behavior.

### 4.8 Preserve deferrals

Features explicitly deferred in Phase 02 must remain deferred.

Do not reintroduce them indirectly through the specification.

Use semantic judgment rather than keyword matching. A price snapshot, for example, does not automatically mean a payment system has entered scope.

### 4.9 Implementation-detail test

For prescriptive details, ask:

> Is this detail necessary to define observable behavior or an approved constraint, or is it merely one of several valid implementation approaches?

Prefer specifying the behavior and required semantics while leaving unnecessary implementation choices to engineering.

For example:

```text
Required behavior:
A draft persists across reload where the approved scope requires it.

Potential implementation detail:
Store it specifically in localStorage.
```

The second should not become a product requirement without a real reason.

### 4.10 Testability

Important requirements should be precise enough that later evidence can demonstrate whether they were satisfied.

Avoid vague requirements such as:

> The workflow should feel reliable.

Prefer observable semantics such as:

> If a submission outcome is unknown, reconcile the existing attempt before allowing a safe retry.

The Guide does not need to design the entire test suite during this review, but it should flag requirements whose completion cannot be meaningfully assessed.

### 4.11 Traceability

The specification should preserve provenance for important requirements sufficiently to support this chain:

```text
Decision Area
      ↓
Spec Requirement / Section
      ↓
Implementation Ticket
      ↓
Acceptance Evidence
```

Do not overload every sentence with metadata, but important behavior must not become detached from its source.

---

## 5. Specification review outcomes

After review, the Guide should recommend one of three outcomes.

### APPROVE

The specification faithfully captures the approved product definition and is ready for decomposition.

### REVISE SPEC

The necessary product decisions exist, but their translation is incomplete, contradictory, vague, or unnecessarily implementation-specific.

Revise the specification and review again.

### RETURN TO PHASE 02

A genuine product ambiguity exists and the specification would have to invent an important rule.

Reopen only the relevant decision area, resolve it explicitly, update downstream artifacts, and then resume specification.

### Specification approval gate

Before running `to-tickets`, answer yes to:

> **Could two competent frontend implementers use this spec and agree on the important observable product behavior, while still retaining reasonable freedom over implementation details?**

If no, decomposition is premature.

---

# Part II — Ticket Decomposition

## 6. Decomposition objective

Once the specification is explicitly approved, `to-tickets` converts one coherent specification into an incremental implementation plan.

> **A good ticket is the smallest coherent unit of product progress that can be implemented, verified, and reviewed without redefining the product.**

The ticket breakdown should guide engineering work; it should not merely divide the specification into arbitrary document sections.

---

## 7. Organize tickets around outcomes

Prefer capability-oriented tickets such as:

- complete a meaningful user workflow
- recover a specific failure mode
- restore and isolate a session
- safely perform a domain mutation

Avoid using purely technical activities as the primary ticket outcome when they are merely parts of delivering a capability.

For example, component creation, hooks, mock API changes, and tests can all be implementation work inside a coherent behavior-oriented ticket.

---

## 8. Prefer vertical slices

Where practical, a ticket should own the relevant slice through the frontend stack:

```text
Behavior
├── domain/mock/API work
├── UI
├── meaningful states
├── automated evidence
└── relevant manual acceptance
```

Avoid automatically splitting API, UI, error handling, and tests into separate tickets if they only become meaningful together.

Split horizontally only when a genuine dependency, risk, reuse boundary, or ticket size justifies it.

---

## 9. Granularity test

For each proposed ticket, ask:

> Can one engineering agent reasonably understand, implement, verify, and report evidence for this ticket in a focused execution cycle?

If one ticket contains several independent capabilities, consider splitting it.

If several tickets have no coherent value or verification boundary until combined, consider merging them.

There is no preferred ticket count. Ten, twenty-five, or fifty tickets can all be valid depending on the specification.

Do not optimize a sound decomposition merely to reach a prettier number.

---

## 10. Dependencies versus preferred order

A blocker is a genuine prerequisite, not merely the ticket that happens to appear earlier in the list.

Use a blocking dependency when a later ticket cannot reasonably be implemented or verified until an earlier capability or contract exists.

Distinguish:

- **BLOCKER** — cannot reasonably proceed first
- **PREFERRED ORDER** — could proceed independently, but sequencing has practical advantages

This distinction preserves opportunities for safe parallel work and avoids creating an artificial `1 → 2 → 3 → 4` chain.

---

## 11. Foundation tickets

Foundation tickets are acceptable when later work genuinely depends on shared groundwork, for example:

- contract/error conventions
- deterministic mock controls
- browser-test foundations

Keep foundations minimal and demand-driven.

Avoid a first ticket whose real purpose is to redesign or refactor the entire frontend architecture before any product capability is delivered.

Build shared infrastructure because concrete tickets require it, not because future abstractions can be imagined.

---

## 12. Tickets cannot make new product decisions

Ticket decomposition must preserve the approved specification.

If a ticket would need to assume an unresolved business rule for implementation convenience, stop and classify the problem:

```text
Missing behavior
    ↓
Spec gap?
    ↓
Decision gap?
    ↓
Resolve upstream
```

Tickets are not a place to hide ambiguity.

---

## 13. Scope boundaries

Each ticket must make its delivery boundary clear enough that the implementation agent understands what belongs in the ticket and what does not.

This can be expressed through explicit `in scope / out of scope` sections or through equally clear acceptance language.

The purpose is to prevent scope creep during implementation, not to add unnecessary bureaucracy.

---

## 14. Acceptance and evidence

A ticket should identify what evidence is expected to demonstrate completion.

Depending on behavior and risk, this may include:

- focused rule/unit evidence
- feature/API integration evidence
- browser-flow evidence
- manual accessibility/responsive/RTL checks
- recovery/failure-state evidence

Do not require every evidence layer for every ticket.

> **Evidence should match the behavior and risk of the ticket.**

### Manual acceptance remains explicit

Automated implementation success does not automatically mean full acceptance.

Preserve distinctions such as:

```text
IMPLEMENTED
≠
AUTOMATICALLY VERIFIED
≠
MANUALLY ACCEPTED
```

If human verification remains outstanding, ticket/project state should make that visible.

---

## 15. Preserve backend implications

Where frontend behavior depends on a production-sensitive guarantee, tickets may preserve the distinction between:

```text
Mock responsibility
→ simulate the approved semantics

Future backend responsibility
→ guarantee those semantics in production
```

Do not design the backend mechanism during frontend ticket decomposition.

---

## 16. Build shared infrastructure opportunistically

When actual tickets reveal a shared primitive, create the minimum reusable infrastructure needed by those tickets.

Avoid predicting every future abstraction and building an internal framework before concrete product work demands it.

The goal is to improve the prototype incrementally rather than replacing it with a speculative architecture rewrite.

---

## 17. Coverage review

After decomposition, verify that important specification requirements have implementation ownership.

The desired chain is:

```text
Spec requirement
      ↓
one or more implementation tickets
      ↓
eventual acceptance evidence
```

Flag:

- **missing ownership** — a requirement has no ticket
- **unnecessary overlap** — multiple tickets own the same behavior without a clear reason
- **scope invention** — a ticket delivers behavior absent from the approved spec

---

## 18. Guide review of `to-tickets`

Review the proposed breakdown for:

- granularity
- coherent outcomes
- vertical slicing
- genuine dependencies
- preferred sequencing
- specification coverage
- duplication
- scope fidelity
- testability
- acceptance evidence
- backend-boundary preservation
- safe opportunities for parallel work

Do not redesign a good decomposition merely because another valid decomposition exists.

If the proposed breakdown is sound, approval can be extremely concise.

For example:

> The 25-ticket granularity is approved.

### Decomposition approval gate

The decomposition agent should pause for user approval before publication/finalization when the workflow requires it.

The Guide should recommend either:

- **APPROVE**
- **CHANGE specific tickets** — identify only the ticket numbers/areas that actually need revision

Do not turn a simple approval into unnecessary planning work.

---

# Part III — Artifacts, Traceability & Handoff

## 19. Canonical traceability chain

Phase 03 should leave a navigable chain:

```text
Phase 02 Decision
        ↓
Frontend Specification
        ↓
Implementation Ticket
        ↓
Implementation
        ↓
Acceptance Evidence
```

The first three layers exist by the end of this phase. Implementation and actual evidence belong to Phase 04 and later acceptance work.

---

## 20. Artifact authority

### Decision artifacts

Decision artifacts remain the source of truth for why important product behavior was chosen.

Do not delete or overwrite their history merely because a consolidated spec now exists.

### Frontend specification

The approved spec is the coherent implementation-facing expression of those decisions.

The authority direction is:

```text
Approved Product Decisions
          ↓
         Spec
          ↓
       Tickets
```

A ticket must not override the spec, and the spec must not silently override an approved product decision.

### Implementation tickets

Tickets are execution units. They should make it possible to understand:

- why the work exists
- what coherent capability it delivers
- what genuine blockers it has
- what evidence should demonstrate completion

Keep traceability useful rather than bureaucratically exhaustive.

---

## 21. Acceptance matrix status

Phase 03 may create or extend a planned requirement-to-evidence matrix.

At this point it records **planned evidence**, not successful verification.

For example:

```text
Requirement
→ Planned evidence
→ Owning ticket
→ Status: NOT VERIFIED
```

Never mark unperformed checks as passed.

Preserve the distinction:

```text
PLANNED EVIDENCE
≠
IMPLEMENTED
≠
VERIFIED
≠
MANUALLY ACCEPTED
```

---

## 22. Project Tracker update

When Phase 03 is complete, update the central project tracker in the playbook to reflect workflow state and navigation.

For example:

```text
Phase 01 — COMPLETE
Phase 02 — COMPLETE
Phase 03 — COMPLETE
Phase 04 — READY TO START

Current frontier:
Frontend Engineering / Ticket 01
```

Do not duplicate the entire specification or ticket system into the central playbook.

Use this separation:

```text
Playbook repository
→ workflow state, guidance, navigation

Product repository
→ project decisions, spec, tickets, implementation evidence
```

This avoids creating competing sources of truth.

---

## 23. Phase 04 handoff package

Before implementation begins, a new engineering agent should be able to locate, from the product repository:

- resolved decisions
- approved frontend specification
- approved implementation tickets
- dependency/order information
- planned acceptance evidence

The next agent should not need the original chat history to understand the current task.

A fresh Guide LLM session should be able to recover context through:

```text
MASTER.md
    ↓
Project Tracker
    ↓
Phase 04 Guide
    ↓
Product Repository
    ↓
Approved Spec
    ↓
Current Ticket
```

> **Chat history must not be a critical dependency of the workflow.**

---

## 24. Final integrity check

Before declaring Phase 03 complete, verify:

- Phase 02 decisions are resolved and available
- the frontend specification is explicitly approved
- every important requirement has implementation ownership
- ticket dependencies/order are sensible
- planned acceptance evidence is identified
- important requirements remain traceable to their source decisions
- a new agent can resume from repository artifacts without relying on chat history
- implementation has not been started as part of this planning phase

If these conditions hold, Phase 03 is complete.

---

## 25. Guide LLM responsibilities in this phase

The Guide LLM should:

- review `to-spec` output for fidelity, completeness, consistency, boundaries, and testability
- distinguish spec gaps from product decision gaps
- return genuine decision gaps to the relevant Phase 02 area
- prevent specification agents from inventing product requirements
- protect approved deferrals and backend boundaries
- review `to-tickets` output for coherent outcomes, granularity, dependencies, coverage, and evidence expectations
- recommend concise approval when a decomposition is already good
- protect traceability from decision through specification to tickets
- help ensure the Project Tracker points to the correct current frontier

The Guide LLM should **not**:

- implement or refactor the frontend
- rewrite a sound specification merely for stylistic preference
- invent missing product behavior
- prescribe unnecessary technical implementation choices
- optimize a sound ticket count for aesthetics
- design the production backend
- claim planned evidence has already passed
- allow implementation to begin before the planning artifacts are approved

---

## 26. Exit criteria

Phase 03 is complete when:

- the Phase 02 decisions have been faithfully compiled into an approved frontend specification
- the specification contains no known unresolved product decision that would force implementation to guess important behavior
- the approved specification has been decomposed into an approved implementation plan
- tickets have coherent scope and meaningful evidence expectations
- dependencies and preferred order are understandable
- important specification requirements have ticket ownership
- traceability exists from decisions to spec to tickets
- planned evidence is distinguished from actual verification
- the Project Tracker can identify Phase 04 as the next frontier
- no application implementation was performed as part of Phase 03

At that point, stop planning and move to frontend engineering.

---

## 27. Transition to Phase 04

Phase 04 is **Frontend Engineering**.

It executes the approved implementation tickets incrementally against the approved specification while preserving evidence, human acceptance gates, and the product/backend boundary.

The governing document will be:

[`04-frontend-engineering.md`](04-frontend-engineering.md)

Do not invent the Phase 04 procedure from this document. Follow its dedicated guide once that guide has been deliberately designed and approved.
