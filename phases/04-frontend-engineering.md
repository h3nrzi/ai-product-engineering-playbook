# Phase 04 — Frontend Engineering

## Purpose

Implement the approved frontend tickets until the frontend is accepted.

The operational workflow is intentionally small:

```text
Approved tickets
      ↓
Implement next ready ticket
      ↓
Verify what matters for that ticket
      ↓
Fix / clarify only if needed
      ↓
Accept ticket
      ↓
Next ticket
      ↓
Final frontend check
      ↓
FRONTEND ACCEPTED
```

> **Phase 04 is ticket execution, not another planning phase.**

## Entry criteria

Start when Phase 03 has an approved frontend specification and approved ticket breakdown, and the product repository is runnable enough to continue engineering.

## 1. Implement tickets one by one

The current ticket is the normal execution boundary. Give the engineering agent the approved ticket and let it inspect the relevant repository state, implement the work, add/update appropriate tests, and report what changed and what was verified.

Do not micromanage ordinary code-level choices. The agent may refactor locally or introduce small shared primitives when needed to deliver the ticket safely.

> **Agent owns implementation choices. It does not own product choices.**

If implementation would materially change approved product behavior, expand scope, or contradict the spec, stop and resolve that specific issue rather than silently changing the product.

## 2. Verification should be proportional

For each ticket, run the checks that meaningfully support its acceptance and the project's existing quality gates. Depending on the ticket this may include focused tests, integration tests, browser flows, build/type/lint checks, or a relevant manual check.

Do not require every possible evidence layer for every ticket.

Keep claims honest:

```text
implemented ≠ tested ≠ manually verified ≠ production guaranteed
```

If a required check was not run, say so. If a mock simulates behavior that a future real server must guarantee, do not present the simulation as a production guarantee.

The purpose of evidence is to decide whether the ticket is safe to accept and continue—not to maximize documentation.

## 3. When something goes wrong

Use the smallest correction that resolves the real problem:

```text
Code/implementation issue → fix locally
Ticket problem → correct the ticket
Spec translation problem → correct the spec
Missing product decision → resolve only that decision
```

Do not reopen the entire workflow for a local problem.

Do not expand the current ticket merely because the agent discovered an unrelated improvement. Record/defer it when useful.

## 4. Session continuity

Repository state should be sufficient for another agent/session to continue without depending on chat history.

If a ticket is left partial or blocked, record only the useful continuation state: what is done, what remains, what is blocked, and the next action. Avoid development diaries and unnecessary process artifacts.

Never discard unexplained existing work merely to obtain a clean working tree.

## 5. Ticket acceptance

A ticket can be accepted when its approved behavior is implemented, the checks actually required for that slice are satisfactory, no ticket-caused blocker remains, and any known limitations are represented honestly.

Use statuses only as much as useful (`in progress`, `blocked`, `ready for human`, `accepted`, etc.). Do not create status ceremony when a simple closed/complete state is sufficient.

Then move to the next ready ticket.

## 6. Final frontend acceptance

After all implementation tickets are complete, perform the project's final agreed frontend checks. The goal is to verify that the important journeys still work together, not to repeat every ticket-level test mechanically.

Close any real defects discovered. Keep unperformed required checks explicit rather than turning them into ceremonial passes.

The frontend is accepted when the approved frontend behavior is implemented, relevant quality gates/checks are satisfactory, blocking defects are resolved or explicitly accepted, and no known product ambiguity prevents trustworthy use of the frontend.

`Frontend Accepted` is a valid stopping milestone for the current playbook.

## 7. Future server/full-stack boundary

The frontend may currently use mocks or demo adapters. Their job is to model intended behavior, not prove production guarantees such as real authorization, persistence durability, atomic concurrency, or external delivery.

Preserve enough clarity about these responsibilities for future server-side work, but do not design that future implementation during Phase 04.

For service-oriented projects, the current strategic default is an integrated **full-stack Next.js** application rather than a mandatory separate backend service. When a Frontend Accepted project is deliberately chosen to continue, design the next phase just in time. That future work may replace mock boundaries with real Next.js server-side behavior and database integration while preserving established product semantics.

A separate backend (for example NestJS/Express) is not assumed; use one only if the project's real requirements or an explicit user decision justify it.

## Guide behavior

The Guide should help answer questions, review agent output, catch contradictions/scope creep, and determine whether it is safe to continue.

The Guide should not turn each ticket into a new planning exercise, demand exhaustive evidence without a project reason, prescribe ordinary implementation details, or create additional documents simply because a protocol could be documented.

## Exit criteria

Phase 04 is complete when all approved frontend tickets are accepted, final agreed frontend checks are satisfactory, blocking defects/ambiguities are resolved or explicitly accepted, and the project can be honestly marked **Frontend Accepted**.
