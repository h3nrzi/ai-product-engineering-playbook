# Phase 02 — Module-by-Module Engineering

## Objective

Build the active Product Delivery Phase one PRD module at a time using the Matt Pocock / AI Hero engineering methodology.

Official reference: <https://www.aihero.dev/>

This phase is where architecture and implementation decisions happen.

The PRD defines **what** the module must accomplish. The engineering conversation decides **how** to build it inside the actual codebase.

---

# Module loop

For each ready PRD module:

```text
01 Select next ready module
        ↓
02 grill-with-docs
        ↓
03 resolve engineering / architecture questions
        ↓
04 choose execution depth
        ↓
05 implement
        ↓
06 code-review
        ↓
07 module acceptance / evidence
        ↓
08 mark complete and select next module
```

Do not begin multiple dependent modules just because they exist in the PRD.

---

# Step 01 — Select the next ready module

Read:

- the project tracker;
- the PRD;
- the active Product Delivery Phase;
- the module brief;
- its dependencies;
- the implementation repository.

A module is ready when its required dependencies are sufficiently settled for engineering to proceed.

Prefer dependency-aware order, but allow independent modules to progress independently when that helps.

Record the current module in the tracker.

---

# Step 02 — Run `grill-with-docs`

Use `grill-with-docs` as the default engineering interview for a module that can be reasoned through in one planning session.

The agent should read the codebase and the PRD/module brief before asking questions.

Questions may cover, when relevant:

- module boundaries;
- data ownership;
- public/internal interfaces;
- state and lifecycle semantics;
- persistence;
- validation authority;
- authentication/authorization;
- concurrency and consistency;
- failure/retry behavior;
- integration boundaries;
- migration/compatibility;
- testing strategy;
- observability/audit needs;
- deployment/runtime constraints.

Do not force all of these topics onto every module.

The interview should resolve the decisions the module actually needs.

## Guide role

For each question from the engineering agent:

1. explain the decision in plain language;
2. show the meaningful trade-offs;
3. connect it to PRD behavior and previous durable decisions;
4. recommend the option that best fits the product/codebase;
5. give the user a concise answer to send back.

If the agent asks something it can learn from the repository, prefer inspecting the repository rather than making the user answer it.

## Durable documentation

Let `grill-with-docs` maintain durable vocabulary/ADRs when a decision genuinely qualifies.

Do not create ADRs for ordinary implementation choices.

---

# Step 03 — Decide how much process the module needs

Use the smallest sufficient path.

## Small / bounded module

If the plan is settled and implementation fits comfortably in one fresh context window:

```text
grill-with-docs
→ implement
→ code-review
```

Do not create a spec and ticket stack just because the tools exist.

## Larger module

If the work must survive multiple implementation sessions:

```text
grill-with-docs
→ to-spec
→ to-tickets
→ implement tickets
→ code-review
```

`to-spec` preserves settled decisions across context boundaries.

`to-tickets` should split the work into small vertical/tracer-bullet slices that can be demonstrated independently.

Avoid horizontal ticket sets such as:

- database first;
- API second;
- UI third;

when those pieces only become useful after all layers land.

## Too large for one planning session

If the module or initiative is itself too large to settle in one planning session, use `wayfinder` to map it first, then resolve the resulting decision areas and feed the settled work into the normal build chain.

Do not use Wayfinder by default for ordinary modules.

## Evidence-seeking work

Use `prototype` or `research` when a genuine unanswered question needs evidence before committing to a design.

Prototype code is learning code, not production code by default.

---

# Step 04 — Specification (when needed)

A module spec is an engineering decision record, not a second PRD.

It should preserve:

- the module's product intent from the PRD;
- architecture decisions resolved during grilling;
- boundaries and interfaces;
- important invariants;
- failure/recovery semantics;
- verification expectations;
- deliberately rejected alternatives when useful.

Do not repeat unrelated product context.

Do not silently change the PRD.

If engineering discovers a product contradiction, return that exact issue to the user and update the PRD deliberately before implementation proceeds.

---

# Step 05 — Tickets (when needed)

Tickets should be agent-ready and sized for fresh implementation sessions.

Each ticket should:

- own one narrow, demonstrable behavior;
- state blockers/dependencies;
- include acceptance criteria;
- preserve relevant module invariants;
- avoid assuming hidden conversation context.

Prefer vertical slices through the required layers.

Avoid creating tickets solely for documents, folders, or architecture layers unless they independently unlock real work.

---

# Step 06 — Implementation

Use `implement` for settled work.

Implementation should follow the module spec/ticket and repository standards.

The implementation agent owns ordinary code-level choices that were not elevated into product/architecture decisions.

Do not interrupt implementation to re-litigate already-settled product behavior.

Where appropriate, verify:

- types/static checks;
- relevant tests;
- integration behavior;
- migration compatibility;
- failure/recovery paths;
- permissions;
- accessibility/interaction behavior for user-facing work.

The exact evidence depends on the module.

---

# Step 07 — Code review

Use `code-review` against an explicit fixed point.

Review two separate questions:

1. Does the change follow repository/code standards?
2. Does the change satisfy the originating spec/ticket/module requirement?

Treat findings as leads that require judgement, not an infinite loop that must reach zero findings.

For larger modules, per-ticket review plus a final integrated review is preferred when practical.

---

# Step 08 — Module acceptance

A module is complete when:

- its required product behavior is implemented;
- module-level acceptance criteria are met;
- relevant tests/checks pass;
- important failure/permission/state behavior is demonstrated where applicable;
- review findings that matter have been resolved or explicitly accepted;
- durable decisions/specs/tickets/evidence are discoverable;
- the tracker marks the module complete.

Do not mark completion based only on code being written.

---

# Cross-module integration

As modules accumulate, verify shared invariants from the PRD.

Examples may include:

- identity and ownership;
- shared status/state semantics;
- money/currency rules;
- time-zone/date rules;
- permissions;
- availability/conflict rules;
- audit/event semantics;
- shared UI navigation or terminology.

Do not wait until the last module to notice that modules disagree on core product semantics.

---

# Completing a Product Delivery Phase

When every required module in the active Product Delivery Phase is complete:

1. run integrated verification across the phase;
2. compare the result with the PRD phase exit condition;
3. close genuine gaps;
4. mark that Product Delivery Phase complete.

If another Product Delivery Phase is next:

- return to the PRD;
- expand that next phase into detailed modules;
- update dependencies/status;
- continue Phase 02 module by module.

Do not fully redesign the entire product roadmap each time unless product learning requires it.

---

# Phase 02 exit criteria

Phase 02 is complete when the intended product delivery roadmap has been implemented to the project's chosen stopping point and the current product is functionally coherent enough for final presentation/use.

Then evaluate visual quality.

If redesign is needed, proceed to [`03-visual-redesign.md`](03-visual-redesign.md).

If the interface is already strong enough, Phase 03 may be minimal or skipped.

---

# Phase principle

> **One module enters with product intent. It leaves as reviewed working software.**
