# Phase 03 — Frontend Specification & Decomposition

## Purpose

Turn the resolved frontend product decisions into an implementation-ready specification and then into executable tickets.

This phase is intentionally simple:

```text
Resolved Wayfinder decisions
        ↓
      to-spec
        ↓
Review + approve spec
        ↓
     to-tickets
        ↓
Review + approve tickets
        ↓
Phase 04 implementation
```

> **Phase 03 is compilation and decomposition, not another discovery phase.**

## Entry criteria

Start when Wayfinder/product-definition work has answered the important questions needed to complete the frontend. The prototype/repository and resolved decisions should be available to the specification agent.

Do not wait for hypothetical future backend decisions that are unnecessary for frontend behavior.

## 1. Run `to-spec`

Use the approved product decisions and prototype context to create the frontend specification.

The spec should preserve approved user-visible behavior and important domain semantics, use consistent vocabulary, preserve explicit scope and deferrals, make important workflows precise enough to implement/test, distinguish mock/demo behavior from guarantees a future real server implementation must provide, and avoid unnecessary prescriptions about components, libraries, database design, API transport, or server architecture.

The prototype is evidence, not authority. If prototype behavior conflicts with an approved decision, the approved decision wins.

### Review the spec

Check only what materially matters:

- Does it faithfully represent the decisions?
- Did it invent important behavior?
- Did it omit or distort an important decision?
- Is there a genuine unresolved product question that would force implementation to guess?
- Is it clear enough to implement?

Classify problems simply:

```text
Spec translation problem → fix the spec
Missing product decision → resolve the relevant decision
No meaningful problem → approve
```

Do not create a large review ritual when the spec is already sound. Before `to-tickets`, explicitly approve the specification.

## 2. Run `to-tickets`

After spec approval, use `to-tickets` to create coherent implementation units. Prefer tickets that deliver meaningful capabilities or workflow slices rather than arbitrary file/component tasks.

A useful ticket should generally be understandable, implementable, verifiable, and reviewable in a focused engineering cycle.

Review the proposed breakdown for sensible granularity, scope fidelity, genuine dependencies/blockers, coverage of important spec behavior, unnecessary duplication, and obvious missing work.

There is no preferred ticket count. If the breakdown is good, approve it concisely rather than redesigning it for stylistic reasons.

Example:

> The 25-ticket granularity is approved.

If something needs changing, identify the specific tickets/areas rather than reopening the whole plan.

## 3. Handoff to implementation

After ticket approval, Phase 03 is complete.

```text
Wayfinder decisions
      ↓
Frontend spec
      ↓
Implementation tickets
      ↓
Phase 04 implementation
```

Detailed acceptance evidence is produced while tickets are implemented; Phase 03 does not need to pre-document every possible future check unless the project genuinely requires it.

## Guardrails

- Do not let `to-spec` invent missing product decisions.
- Do not let `to-tickets` redefine the approved spec.
- Do not prescribe implementation details without a real constraint.
- Do not manufacture edge cases or documentation merely for completeness.
- Preserve important frontend/server responsibility boundaries, but do not design the future server implementation here.
- Keep the process proportional to the project.

## Exit criteria

Phase 03 is complete when the frontend specification and ticket breakdown are approved, important behavior has clear implementation ownership, and no known product ambiguity blocks implementation.

Then proceed directly to **Phase 04 — Frontend Engineering**.
