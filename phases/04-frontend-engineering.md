# Phase 04 — Frontend Engineering

## Purpose

Execute the approved frontend implementation tickets one at a time, preserve the approved product semantics, verify what was actually achieved, and leave enough durable evidence and repository state for another agent to continue without relying on chat history.

This is the first phase in which application implementation begins.

> **Execute one approved ticket at a time, preserve the approved product semantics, verify what was actually achieved, and never let implementation silently redefine the product.**

The Guide LLM remains a guide and reviewer rather than the implementation agent.

> **Agent owns implementation choices. It does not own product choices.**

---

## Phase boundary

```text
PHASE 03 — APPROVED SPEC + TICKETS
        ↓
SELECT NEXT READY TICKET
        ↓
IMPLEMENT
        ↓
VERIFY + RECORD EVIDENCE
        ↓
GUIDE / HUMAN REVIEW AS REQUIRED
        ↓
ACCEPT OR RECOVER
        ↓
NEXT READY TICKET
        ↓
ALL TICKETS ACCEPTED
        ↓
FINAL PRODUCT VERIFICATION
        ↓
FRONTEND ACCEPTED
        ↓
BACKEND HANDOFF
```

---

## 1. Entry criteria

Phase 04 begins when the project has:

- an approved frontend specification
- approved implementation tickets
- understood blockers/dependencies and preferred order
- planned acceptance evidence
- a runnable repository
- at least one ready implementation ticket

The approved hierarchy remains:

```text
Approved Decisions
        ↓
Approved Spec
        ↓
Current Ticket
        ↓
Implementation
```

If a ticket conflicts with the spec, investigate and correct the ticket. If the spec conflicts with an approved decision, correct the downstream artifact rather than silently changing the decision in code.

---

## 2. Ticket Execution Loop

Work through ready tickets incrementally.

```text
Select next ready ticket
        ↓
Read ticket and relevant spec
        ↓
Inspect relevant implementation
        ↓
Plan locally
        ↓
Implement
        ↓
Run required automated verification
        ↓
Collect evidence
        ↓
Agent reports result
        ↓
Guide reviews result
        ↓
Human acceptance if required
        ↓
Close/accept ticket
        ↓
Select next ready ticket
```

Do not hand the entire implementation plan to the agent as one undifferentiated coding task.

### Ticket as execution boundary

The current ticket is the primary execution boundary. The agent may inspect nearby code, refactor locally, add/update tests, adjust necessary shared primitives, and fix directly caused regressions when these actions serve the ticket.

> **Refactor in service of the ticket, not instead of the ticket.**

Do not use a ticket as an excuse to redesign unrelated areas of the application.

---

# Part I — Implementation Change Protocol

## 3. Three levels of implementation change

Classify changes encountered during ticket execution as:

```text
LEVEL 1 — IMPLEMENT FREELY
LEVEL 2 — IMPLEMENT + REPORT
LEVEL 3 — STOP + ESCALATE
```

### Level 1 — Implement freely

The agent may make local engineering choices that do not change approved observable product behavior, such as:

- extracting helpers
- renaming internal symbols
- splitting components
- removing local duplication
- reorganizing local state
- adding focused tests
- improving internal type/checking annotations
- replacing an internal implementation detail
- small local cleanup

These changes are permitted when ticket scope and spec behavior remain intact and no unrelated regression is introduced.

### Level 2 — Implement and report

Some engineering changes have a wider footprint but remain necessary implementation choices, for example:

- a shared error primitive
- common adapter behavior
- a shared form utility
- test-fixture extensions
- a small cross-feature refactor required by the ticket

The agent may proceed when approved product semantics do not change, but the final report should explain why the shared change was necessary, what surface changed, what else may be affected, and how it was verified.

### Level 3 — Stop and escalate

Stop when proceeding would require changing or inventing product semantics, scope, or an approved guarantee.

Examples include simplifying away an approved recovery behavior, changing retry semantics, adding a new actor/role, or choosing between user-visible behaviors that the approved artifacts do not settle.

---

## 4. Escalation ladder

Do not jump directly to product discovery for every implementation question.

Use the nearest authoritative layer that can resolve the issue:

```text
Implementation issue
        ↓
fix locally

Ticket/dependency issue
        ↓
Phase 03 ticket correction

Spec issue
        ↓
Phase 03 spec correction

Decision issue
        ↓
Phase 02 decision reopening
```

If an approved decision already contains the answer but the spec omitted it, correct the spec and affected ticket rather than reopening Phase 02.

If no approved product answer exists and implementation would have to guess important behavior, reopen only the relevant Phase 02 decision, record the new decision, propagate it through the spec and affected tickets, then resume implementation.

---

## 5. Scope expansion

When an agent discovers a potentially useful enhancement during implementation, ask:

1. Is it required by the current ticket?
2. Is it required to preserve the approved spec or prevent a regression?
3. If neither, why is it being added now?

If the answer is only that it would be nice to have, defer it.

> **Good idea ≠ current scope.**

Meaningful future work may be recorded without expanding the current ticket.

---

## 6. Refactoring and technical debt

Refactoring is justified when it is needed to implement the ticket safely, preserve approved behavior, make relevant code testable, remove a concrete blocker, or make a small obvious reduction in implementation risk.

"I would design this differently" is not by itself a reason for a broad rewrite.

The vibe-coded prototype should be engineered incrementally rather than discarded simply because it began as a prototype.

Technical debt that does not block the current ticket should be assessed and recorded when meaningful, then left for appropriate future work. Do not fix the entire codebase because one debt item was discovered.

---

## 7. Behavior-changing bug fixes

Do not assume every surprising prototype behavior is automatically a bug.

```text
Prototype behavior
       ↓
Approved behavior exists?
       ↓
YES → fix against approved behavior
NO  → potential decision gap
```

> **Prototype behavior is evidence, not authority.**

---

## 8. Dependency/tooling changes

Adding or removing a small dependency may be an ordinary engineering choice. A broad framework, state-management, or architectural migration has a much larger governance impact.

> **Impact determines governance.**

Large cross-cutting choices should be reported and, when they materially alter the implementation strategy or approved constraints, reviewed before proceeding.

---

# Part II — Verification & Evidence Protocol

## 9. Evidence principle

> **Completion claims must never be stronger than the evidence that supports them.**

Keep these concepts distinct:

```text
IMPLEMENTED
    ↓
AUTOMATED VERIFIED
    ↓
MANUALLY VERIFIED
    ↓
ACCEPTED
```

They are not synonyms.

Evidence requirements come from the approved spec, current ticket, and project quality gates. Do not impose the same ritual on every ticket.

> **Evidence depth follows behavior, risk, and approved acceptance requirements.**

---

## 10. Automated evidence

Depending on the ticket, automated evidence may include:

- static/type/checkJs checks
- lint/build
- focused rule tests
- feature/API integration tests
- browser journey tests
- deterministic edge-case tests
- regression tests

A test should directly support the acceptance claim being made. The existence of a passing test is not sufficient if it does not exercise the relevant behavior.

### Deterministic evidence

When approved behavior depends on time, races, storage, stale data, failures, or uncertain outcomes, prefer repeatable controls such as:

- controlled clocks
- resettable fixtures
- forced failures
- delayed responses
- stale revisions
- slot loss
- unknown outcomes
- missing/corrupt/unavailable storage

Use deterministic evidence when the approved quality plan requires it rather than relying only on manual repetition.

---

## 11. Manual evidence

Some acceptance concerns may require human checks, including:

- visual coherence
- responsive behavior
- RTL quality
- keyboard usability
- visible focus
- screen-reader experience
- real-device behavior
- content clarity

Automation and emulation can support these checks but must not be misrepresented as the real environment when the distinction matters.

Examples:

```text
Playwright mobile emulation
≠ real Android Chrome

Playwright WebKit
≠ real iOS Safari

Mock concurrency simulation
≠ production backend concurrency guarantee

Simulated OTP
≠ real SMS delivery
```

---

## 12. Evidence records

A ticket report should make it possible to determine:

- what changed
- what was tested
- what passed
- what was not run
- what manual checks remain
- whether any exceptions were explicitly accepted

Reports should be concise and evidence-focused rather than development diaries.

Never convert a planned check into a claimed check.

Avoid inflated claims such as "fully verified," "production-safe," "works on all browsers," or "accessibility complete" unless the recorded evidence actually supports them.

---

## 13. Existing failures and exceptions

When verification finds a failure, determine whether the current ticket caused it.

```text
Failure
  ↓
Caused by current ticket?
  ├─ YES → fix before completion
  └─ NO  → document
             ↓
       Does approved quality gate block on it?
          ├─ YES → block
          └─ NO  → continue with explicit record
```

If a required check cannot be performed, record it as `NOT PERFORMED`/`NOT RUN`, explain why, and state what remains required. Do not infer a pass from a related simulation.

An explicitly user/project-approved exception should remain distinguishable from `PASS`.

---

## 14. Evidence history and regression responsibility

> **Later work may supersede evidence, but should not rewrite history.**

When a later ticket changes behavior covered by earlier evidence, preserve the earlier record and mark it stale/superseded where appropriate, then create new verification evidence.

Conceptually distinguish:

```text
VALID EVIDENCE
STALE / SUPERSEDED EVIDENCE
NOT YET VERIFIED
```

Each ticket should verify not only its new behavior but also affected existing behavior in proportion to its change footprint.

> **Regression scope should follow the change footprint.**

The final phase gate will run broader product-level verification.

---

## 15. Ticket status vocabulary

Use a shared vocabulary such as:

- `READY`
- `IN PROGRESS`
- `IMPLEMENTED`
- `READY FOR HUMAN`
- `ACCEPTED`
- `BLOCKED`
- `REOPENED`

`IMPLEMENTED` means the implementation and required automated work for the current stage are complete, while human acceptance may still remain.

`READY FOR HUMAN` means the implementation/evidence is ready and one or more specified human checks remain.

`ACCEPTED` means required ticket acceptance has been completed or required exceptions have been explicitly accepted.

Do not use an ambiguous `done` when the distinction matters.

---

# Part III — Ticket Progression & Recovery Protocol

## 16. Ticket lifecycle

A normal lifecycle is:

```text
READY
  ↓
IN PROGRESS
  ↓
IMPLEMENTED
  ↓
READY FOR HUMAN   ← when required
  ↓
ACCEPTED
```

Side paths include:

```text
IN PROGRESS → BLOCKED → IN PROGRESS

IMPLEMENTED / READY FOR HUMAN / ACCEPTED
                ↓
             REOPENED
                ↓
           IN PROGRESS
```

An accepted ticket may be reopened for a real regression, later invalidating change, acceptance defect, legitimate upstream decision change, or spec correction that affects its implementation.

Do not reopen accepted work merely because an optional refactor is now imaginable.

---

## 17. Claim before work and partial progress

Before implementation, claim the ticket and make its `IN PROGRESS` state durable.

Partial implementation is legitimate. If a session ends before completion, record concise continuation state, including:

- current ticket/status
- what was implemented
- what remains
- what was verified
- known failures/blockers
- important areas/files touched
- next recommended action

> **Record continuation state, not conversation history.**

---

## 18. Session recovery

A new engineering agent should recover through durable project state:

```text
Project Tracker
      ↓
Current Phase
      ↓
Current Ticket
      ↓
Ticket status / handoff
      ↓
Relevant spec
      ↓
Repository diff/current code
      ↓
Existing evidence
      ↓
Continue
```

The new agent must inspect the actual repository before making further changes. Handoff notes guide recovery, but the repository remains the implementation source of truth.

---

## 19. Blocked tickets

Use `BLOCKED` for a genuine prerequisite that prevents correct continuation, such as:

- a missing approved product decision
- a broken prerequisite ticket
- a required external dependency that is unavailable
- a spec contradiction
- repository state that prevents safe continuation

A blocker record should identify what blocks the ticket, why it blocks, and what resolution is required.

Once resolved, update affected artifacts, remove the blocker, return the ticket to `IN PROGRESS`, and resume.

---

## 20. Dependency changes

Implementation may reveal that the Phase 03 dependency graph was incomplete.

If this is only a decomposition problem, update the ticket/dependency artifact, mark the affected ticket blocked if necessary, execute the prerequisite, and resume. Do not reopen product discovery unnecessarily.

---

## 21. Reopening and impact analysis

When a ticket is reopened:

```text
Reopen ticket
      ↓
Identify affected downstream tickets
      ↓
Identify potentially stale evidence
      ↓
Fix
      ↓
Reverify affected behavior
```

Consider both code dependencies and evidence dependencies. A downstream ticket's code may remain unchanged while its old evidence no longer proves current behavior.

---

## 22. Failed attempts

A failed implementation approach does not mean the ticket itself failed.

Do not record every experiment. Preserve a failed attempt only when its learned constraint is important enough to prevent future agents from repeating a costly or unsafe path.

---

## 23. Dirty repository recovery

A new session may inherit partial or uncommitted work.

Do not automatically reset it, and do not automatically assume every change is intentional.

```text
Inspect diff
↓
Map changes to current ticket/handoff
↓
Preserve understood work
↓
Identify unexplained changes
↓
Continue only when state is understood
```

> **An agent must not discard existing work it cannot attribute or understand merely to obtain a clean working tree.**

If necessary, investigate or escalate before destructive actions.

---

## 24. Parallel tickets

Independent tickets may be executed in parallel when the dependency graph permits it, but ownership and evidence must remain clear for each ticket.

Shared-file collisions or overlapping behavior should be reconciled deliberately rather than allowing parallelism to obscure which ticket owns a change.

---

## 25. Project Tracker during engineering

The central playbook tracker should remain high level. It may record, for example:

```text
Phase 04 — IN PROGRESS
Current frontier: Ticket 08
Progress: 7 accepted, 1 in progress, 17 pending
Blockers: None
```

Detailed execution state and evidence belong in the product repository rather than being duplicated into the central playbook.

### Recovery test

At any session boundary, ask:

> **If chat history disappeared now, could another engineering agent use the SSOT and repository to understand where the project is and continue safely?**

If no, the handoff is incomplete.

---

# Part IV — Phase Completion & Handoff

## 26. Entering final verification

Completing the last implementation ticket does not by itself prove frontend completion.

> **Ticket completion proves the parts. Phase completion proves the product works as an integrated frontend.**

Enter final verification when all implementation tickets are accepted or covered by explicit accepted exceptions, and no unresolved blocker remains.

A ticket still waiting on required human acceptance prevents final frontend acceptance unless the missing check has been explicitly accepted as an exception under the project's quality rules.

---

## 27. Full quality gates

Run the complete set of quality gates approved for the project, which may include:

- build
- typecheck/checkJs
- lint
- rule tests
- integration tests
- browser tests

Do not invent new completion gates at the end of the project. Use the gates approved during product definition/specification.

---

## 28. Cross-feature verification

Verify the major integrated journeys across ticket boundaries.

The purpose is not to duplicate every ticket-level test, but to demonstrate that separately implemented capabilities work together as a product.

Cross-feature journeys should come from the product's approved core workflows and meaningful interactions between public, customer, staff/admin, content, configuration, and other applicable surfaces.

---

## 29. Acceptance matrix closure

The planned acceptance matrix from Phase 03 now becomes an evidence record.

For each requirement, preserve:

```text
Requirement
→ Owning ticket
→ Automated evidence
→ Manual evidence
→ Result
→ Exception / defect
```

Use explicit result states such as:

- `PASS`
- `FAIL`
- `NOT RUN`
- `NOT APPLICABLE`
- `ACCEPTED EXCEPTION`

`NOT RUN` never becomes `PASS` merely because the project is near completion.

> **No ceremonial green checkmarks.**

---

## 30. Manual product acceptance

Run the project-level manual checks that were actually approved for this product. Depending on the project, these may include desktop/mobile behavior, keyboard navigation, RTL, accessibility, screen-reader checks, real-device behavior, timezone behavior, browser support, and failure/recovery UX.

Do not claim an environment was checked when only a simulation or different environment was exercised.

---

## 31. Final defects

If final verification finds a defect:

```text
Defect
  ↓
Identify owning behavior/ticket
  ↓
Reopen relevant ticket
  ↓
Fix
  ↓
Reverify affected behavior
  ↓
Rerun relevant final checks
```

Rerun verification according to impact rather than blindly repeating every check, while keeping the phase open until blocking defects are resolved or explicitly accepted.

---

## 32. Definition of Frontend Complete

Within this workflow, the frontend is complete when:

- approved product behavior is implemented
- required automated gates pass
- required manual acceptance is complete
- known blocking defects are resolved or explicitly accepted under the project's rules
- no unresolved product/spec ambiguity forces implementation to guess important behavior
- mock/demo boundaries are represented honestly
- backend responsibilities remain explicit
- repository evidence supports the completion claims

Frontend completion does **not** mean the entire product is production-ready.

---

## 33. Backend handoff package

The completed frontend should provide the next backend phase with a clear behavioral contract.

The handoff should make it possible to determine:

- what frontend-facing operations exist
- what contracts and semantics the frontend expects
- what domain rules must become authoritative on the backend
- what identity/session and authorization guarantees are required
- what operations must be atomic
- what requires durable persistence
- what revision/idempotency/reconciliation semantics exist
- what mock behavior is only simulation
- what external integrations are still fake or absent
- what concurrency/security/durability guarantees have not been proven by frontend/mock evidence

Do not prescribe database, ORM, cache, locking, or infrastructure mechanisms unless an approved project constraint already requires them.

The handoff specifies required behavior and guarantees; the backend phase decides how to provide them.

---

## 34. Engineered frontend as executable reference

By the end of this phase, the original prototype has evolved through explicit product decisions, specification, implementation, and verification into an engineered frontend with a verified mock adapter.

```text
Original Prototype
        ↓
Product Decisions
        ↓
Specification
        ↓
Engineered Frontend
        ↓
Verified Mock Adapter
```

The frontend/mock combination can act as an executable behavioral reference for backend work, but it is not production authority.

For example, the mock may demonstrate how a booking conflict appears to the user while the backend must later guarantee that concurrent requests cannot double-book the resource.

---

## 35. Adapter conformance path

Where the approved contracts support it, preserve a path toward running the same frontend-facing contract suite against both adapters:

```text
Contract Suite
      │
   ┌──┴──┐
   ▼     ▼
Mock   Backend
Adapter Adapter
```

After backend integration, critical frontend browser journeys should be rerun against the real backend adapter.

Server concurrency, durability, security, and external-integration guarantees still require backend-specific evidence; mock conformance cannot prove them.

---

## 36. Tracker transition

After frontend acceptance, update the project tracker to reflect the completed phase and next frontier, for example:

```text
Phase 01 — COMPLETE
Phase 02 — COMPLETE
Phase 03 — COMPLETE
Phase 04 — COMPLETE

Frontend status: ACCEPTED
Current frontier: Backend Definition
```

The tracker should navigate to the product repository artifacts rather than duplicating their full contents.

---

## 37. Final recovery test

Before closing Phase 04, ask:

> **If all chat history disappeared, could a new agent use the SSOT and product repository to understand what the frontend does, why it behaves that way, what was verified, what remains simulated, and what the backend must provide?**

If no, the handoff is incomplete.

If yes, Phase 04 may be closed.

---

## 38. Guide LLM responsibilities in this phase

The Guide LLM should:

- help interpret the current ticket and approved spec when the user needs guidance
- review agent reports for scope fidelity and evidence quality
- distinguish engineering choices from product choices
- prevent implementation convenience from silently changing approved behavior
- classify discovered issues at the nearest appropriate upstream layer
- help decide whether a ticket is implemented, ready for human review, blocked, accepted, or should be reopened
- challenge evidence claims that are stronger than the recorded checks
- preserve distinctions between simulation and real production guarantees
- help review final acceptance and backend handoff completeness

The Guide LLM should **not**:

- micromanage ordinary engineering details
- prescribe helpers/components/files without a reason tied to the approved behavior
- reopen planning for every implementation difficulty
- accept scope expansion merely because an enhancement is useful
- treat prototype behavior as product authority
- treat automated simulation as evidence of an untested real environment
- mark planned or unperformed checks as passed
- design backend implementation mechanisms during frontend engineering

---

## 39. Exit criteria

Phase 04 is complete when:

- all approved frontend implementation tickets are accepted or covered by explicit accepted exceptions
- required full-project quality gates pass
- approved cross-feature journeys have been verified
- required manual product acceptance is complete
- the acceptance matrix reflects actual evidence and exceptions
- blocking defects are resolved or explicitly accepted
- frontend/mock limitations remain honest and visible
- backend responsibilities and unproven production guarantees are clearly handed off
- the project tracker points to Backend Definition as the next frontier
- another agent can recover the project state without relying on chat history

At that point, the frontend is accepted for this workflow and the project moves to backend definition and engineering through its dedicated phase guide.
