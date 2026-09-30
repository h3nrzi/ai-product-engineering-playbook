# Phase 02 — Frontend Product Definition

## Purpose

Use the prototype as evidence to discover implicit, incomplete, ambiguous, or contradictory product behavior and turn it into explicit, trustworthy decisions before frontend engineering begins.

This phase defines **what the frontend product must mean and do**. It does not implement or refactor the application, and it does not design the production backend.

The Guide LLM defined in [`../MASTER.md`](../MASTER.md) acts as the user's decision analyst and reviewer. The engineering/planning agent (for example, Codex using Wayfinder/grilling-style skills) inspects the product, proposes decision areas, asks questions, and records approved decisions.

The governing relationship is:

> **Agent proposes. Guide analyzes. User decides. Agent records.**

A second governing principle is:

> **The prototype supplies evidence, not answers.**

Prototype behavior may be intentional, provisional, incomplete, or simply a shortcut. Do not promote it to a product requirement without deliberate review.

---

## Phase boundary

```text
PHASE 01 HANDOFF
        ↓
ENTRY CHECK
        ↓
REPOSITORY + PROTOTYPE AUDIT
        ↓
DECISION LANDSCAPE / WAYFINDER
        ↓
DECISION MAP
        ↓
GUIDE REVIEW
        ↓
GRILL DECISION AREAS
        ↓
RESOLVED PRODUCT DECISIONS
        ↓
COVERAGE + CONSISTENCY REVIEW
        ↓
READY-FOR-SPEC CHECK
        ↓
PHASE 03 — FRONTEND SPECIFICATION & DECOMPOSITION
```

---

## 1. Entry criteria

Phase 02 normally begins after the Phase 01 handoff.

The expected starting context is:

- a runnable or inspectable prototype
- a product repository/local project accessible to the engineering agent
- the Prototype Handoff
- identified core journeys
- known prototype assumptions
- known open questions

The following are **not** required at entry:

- final frontend architecture
- final domain model
- final API contracts
- backend architecture
- implementation tickets

Part of this phase exists precisely because those product-facing boundaries may still need clarification.

---

## 2. Repository and prototype audit

Before asking detailed product questions, the engineering agent should inspect the actual prototype and repository.

> Wayfinder should not interrogate a product it has not inspected.

The audit should seek enough evidence to understand areas such as:

- routes and pages
- core journeys
- existing interactions
- mock APIs and data
- identity simulation
- persistence/storage behavior
- customer/user areas
- staff/admin areas where relevant
- forms and mutations
- loading, empty, failure, success, and recovery behavior where present
- responsive behavior
- existing tests
- obvious placeholders or incomplete routes
- dead or inconsistent flows
- Base44/platform-specific dependencies

The audit is for understanding, not rebuilding.

```text
UNDERSTAND
not
REBUILD
```

Do not begin by refactoring the prototype or declaring its architecture wrong.

### Compare evidence sources

Use three sources together:

```text
Prototype Handoff
        +
Actual repository
        +
Actual interactive product
        ↓
Product-definition evidence
```

Differences between the handoff and actual behavior are useful findings. They may expose incomplete journeys, hidden assumptions, or decision areas for Wayfinder.

---

## 3. Build the decision landscape

Do not immediately jump into narrow questions such as exact cutoffs or field rules.

First identify the product's unresolved decision areas and build a Decision Map.

The map must be derived from the product rather than copied from a generic checklist.

Possible areas in one product might include public experience, a core transactional workflow, customer identity, staff operations, domain/API boundaries, quality gates, or backend handoff. Another product may instead require workspace membership, subscriptions, inventory, sellers, collaboration, or other domain-specific areas.

Do not hard-code another project's map into the current product.

### Guide review of the Decision Map

Before detailed grilling begins, the user should bring the proposed map to the Guide LLM.

Review it for:

- **Coverage** — is an important product area missing?
- **Overlap** — are multiple tickets asking essentially the same decision?
- **Granularity** — is an area too broad or unnecessarily fragmented?
- **Prematurity** — has production backend architecture leaked into frontend definition?
- **Product relevance** — did the area arise from this product, or from a generic checklist?

The Guide should either approve the map or recommend only the corrections that are actually needed. It should not recreate the entire Wayfinder process unnecessarily.

---

## 4. Grill decision areas incrementally

Once the Decision Map is approved, work through decision areas one at a time.

A typical loop is:

```text
Claim decision area
        ↓
Agent inspects relevant evidence
        ↓
Agent asks a small batch of questions
        ↓
STOP FOR USER DECISION
        ↓
User brings questions to Guide
        ↓
Guide analyzes
        ↓
User answers Agent
        ↓
Next round if needed
        ↓
Shared-understanding confirmation
        ↓
Agent records the decision
```

Preserve the human decision point. The planning agent should not ask a large set of questions and then silently accept its own recommendations.

---

## 5. Decision Quality Protocol

When the agent asks a question, the Guide should understand the decision before recommending a response.

The default reasoning flow is:

```text
Agent Question
     ↓
1. Classify
     ↓
2. Understand
     ↓
3. Check Context
     ↓
4. Evaluate Options
     ↓
5. Recommend
     ↓
6. Compose Reply
```

### 5.1 Classify the decision

Useful categories include:

- **Product** — what should the product do?
- **UX** — what should the user see or experience?
- **Domain** — what concepts and rules define the product?
- **Frontend contract** — what semantics should frontend-facing operations provide?
- **Quality** — what is required to consider the frontend complete?
- **Backend implication** — what must a future production backend guarantee?
- **Backend architecture** — how exactly should the backend implement the guarantee?

The first six may legitimately appear in Phase 02.

Backend architecture normally belongs to the later backend-definition phase.

For example:

```text
"Booking must be atomic."
→ valid product/backend-responsibility decision

"Use PostgreSQL advisory locks for booking."
→ backend architecture; defer
```

### 5.2 Translate the question

When useful, the Guide should explain in plain language:

> "The agent is really asking whether..."

This helps the user understand the underlying product decision rather than merely accepting the agent's recommended wording.

### 5.3 Check context

Before recommending an answer, compare the question against:

```text
Existing decisions
       +
Prototype behavior
       +
Current scope
```

Check whether:

- the topic has already been decided
- the prototype provides useful evidence
- the recommendation conflicts with earlier decisions
- the capability is actually in scope

### 5.4 Evaluate the agent recommendation independently

`Recommended` does not mean correct by default.

Use three outcomes:

- **AGREE** — the recommendation fits the product and prior decisions
- **ADJUST** — the direction is right but a meaningful boundary should change
- **CHALLENGE** — the recommendation contradicts scope, semantics, or prior decisions

When the recommendation is already good, keep the response simple.

### 5.5 Discuss alternatives only when meaningful

Do not invent multiple alternatives for every question.

Explain alternatives when there is a genuine tradeoff that materially changes product behavior, scope, identity, ownership, or another important concern.

### 5.6 Match analysis depth to decision impact

```text
LOW IMPACT
→ recommendation + short reason

MEDIUM IMPACT
→ consequences + recommendation

HIGH IMPACT
→ meaningful alternatives + interactions + future implications + recommendation
```

Do not turn a simple approval into an architecture exercise.

### 5.7 Know when not to answer yet

The Guide should recommend deferral or reframing when the question is:

- **Premature architecture** — asks for an implementation mechanism that belongs to a later phase
- **Missing product context** — cannot be answered responsibly until a more fundamental requirement is known
- **A false choice** — important alternatives are missing from the framing
- **Hidden scope expansion** — assumes a capability that has not been included in the product scope

### 5.8 Record backend implications without designing the backend

A frontend/product decision may legitimately imply a backend responsibility.

Example:

```text
PRODUCT DECISION
Repeated booking requests must not create duplicates.
        ↓
BACKEND IMPLICATION
The production backend must provide durable idempotency/reconciliation.
        ↓
NOT YET
Choose the persistence table, transaction mechanism, or framework implementation.
```

Preserve the implication for backend handoff; defer the mechanism.

### 5.9 Compose the user's response

For meaningful questions, a useful Guide response may cover:

- what the question is really asking
- why it matters
- the Guide's recommendation
- the concise answer to send to the agent

This is not a mandatory template.

When the recommendation is clearly sound and no nuance is needed, the best guidance may simply be:

> Recommendation is good. Send `Yes.`

---

## 6. Shared-understanding gate

After one or more grilling rounds, the planning agent may summarize the intended decision and ask for confirmation.

Do not approve automatically.

The Guide should compare the summary against what the user actually decided:

- Did it preserve the user's answers?
- Did it add anything that was never approved?
- Did it omit an important boundary?
- Did an agent recommendation silently become a decision?
- Did implementation detail leak into the product decision?

If the summary is faithful, a concise confirmation is sufficient.

If it is not, provide only the corrections needed.

---

## 7. Decision ticket closure

When a decision area is resolved, review the result at an appropriate level.

Check, where relevant, that:

- the decision was actually recorded
- the correct planning artifact was updated
- the decision area is marked resolved
- the Decision Map reflects the new state
- no unintended application implementation occurred
- the next unresolved frontier is identified

Verification depth should be proportional to importance and risk. Do not perform heavyweight repository forensics after every trivial documentation update unless there is a reason.

---

## 8. Decision coverage

Phase 02 should resolve ambiguity that would otherwise force implementation to invent product behavior.

A useful test is:

> If two competent implementers could read the current product definition and legitimately build materially different user-facing behavior, is an important product decision still missing?

If yes, that ambiguity probably belongs in Phase 02.

If the difference is merely a safe implementation detail, it may belong later.

### Three levels of coverage

Ensure the product has been considered across:

- **Product surface** — routes, journeys, actors
- **Behavior** — rules, states, mutations, failure/recovery where meaningful
- **Boundaries** — identity, authority, frontend-facing contracts, quality expectations, backend responsibilities

The exact topics must still come from the product rather than a universal checklist.

### Happy paths are not enough

For important workflows, consider relevant states such as:

- before/action readiness
- in progress/loading
- success
- failure
- empty results
- stale state
- retry
- recovery
- ownership/access

Do not require every state on every page.

> Consider every relevant state; require only the states that are meaningful for that workflow.

---

## 9. Classify remaining open questions

Not every open question must block Phase 02.

Every meaningful unresolved question should have an explicit destination:

- **RESOLVE NOW** — blocks frontend specification
- **DEFER TO BACKEND** — product semantics are known, but production implementation/guarantee is not yet designed
- **DEFER TO LATER PRODUCT SCOPE** — capability is intentionally excluded from the current product phase
- **IMPLEMENTATION DETAIL** — can safely be decided during specification/engineering without redefining the product

Avoid ownerless ambiguity that will be decided accidentally during implementation.

---

## 10. Cross-decision consistency review

After the final decision area is resolved, do not immediately run `to-spec`.

Perform a short consistency review across the resolved decisions.

Look for:

- contradictions between decision areas
- terminology drift
- duplicate concepts with different names
- accidental scope expansion
- prototype assumptions promoted to requirements without approval
- backend architecture accidentally specified
- frontend behavior with unclear authority
- requirements made impossible by another decision
- deferred features still referenced as active

If a conflict is found, reopen only the relevant decision area. Do not restart the entire Wayfinder process.

The Decision Map should accurately show which areas are resolved and which, if any, remain open.

---

## 11. Definition of Ready for frontend specification

Phase 02 is ready to exit when:

- intended frontend scope is explicit
- core journeys have defined behavior
- important mutations have meaningful success/failure/recovery semantics where relevant
- identity and ownership expectations are explicit where relevant
- important domain vocabulary is stable enough for specification
- frontend-facing authority and boundaries are understood
- quality/completion expectations are defined
- backend responsibilities are identified without prematurely designing their implementation
- remaining open questions have explicit destinations
- decision areas are resolved
- cross-decision consistency review passes

The following are **not** required:

- implementation tickets
- final component architecture
- final backend architecture
- database schema
- HTTP endpoint design
- complete test implementation
- production infrastructure

### Final readiness question

Before leaving Phase 02, ask:

> **Could an implementation-spec agent now describe what the frontend must do without inventing important product behavior?**

If **no**, a decision gap remains.

If **yes**, Phase 02 has served its purpose.

---

## 12. Guide LLM responsibilities in this phase

The Guide LLM should:

- help review the repository/prototype audit without taking over implementation
- review the proposed Decision Map
- explain Wayfinder/grilling questions in practical language
- evaluate agent recommendations independently
- compare new questions against prior decisions and scope
- recommend concise answers when the decision is straightforward
- provide deeper tradeoff analysis only when the decision warrants it
- identify premature backend architecture and defer it
- detect hidden scope expansion and false choices
- preserve decision continuity across tickets
- review shared-understanding summaries before approval
- help classify unresolved questions
- help perform the final consistency/readiness review

The Guide LLM should **not**:

- implement or refactor the frontend
- answer every agent question with a long analysis
- blindly accept `Recommended` options
- recreate Wayfinder when the agent's map is already sound
- turn backend implications into backend architecture
- allow prototype shortcuts to become requirements without review
- silently make the user's product decisions

---

## 13. Outputs

The expected Phase 02 outputs are planning artifacts, not application code:

```text
Prototype
+
Prototype Handoff
+
Decision Map
+
Resolved Decision Artifacts
+
Stable Product Vocabulary
+
Explicit Deferrals
+
Backend Responsibility Notes
        ↓
PHASE 03
```

The exact storage structure may depend on the engineering skill/tool in use, but the decisions must remain traceable and reviewable.

---

## 14. Transition to Phase 03

Phase 03 is **Frontend Specification & Decomposition**.

Its job is to faithfully transform the approved decisions into an implementation-ready specification, review that specification, and then decompose the approved specification into implementation tickets.

Phase 03 should not casually reopen product discovery.

If the specification process discovers that it must invent an important business rule in order to proceed:

```text
STOP
 ↓
Decision gap detected
 ↓
Return to the relevant Phase 02 decision
 ↓
Resolve explicitly
 ↓
Update downstream artifacts
 ↓
Resume specification
```

The governing document will be:

[`03-frontend-specification.md`](03-frontend-specification.md)

Do not invent Phase 03 procedure from this document. Follow its dedicated guide once that guide has been deliberately designed and approved.
