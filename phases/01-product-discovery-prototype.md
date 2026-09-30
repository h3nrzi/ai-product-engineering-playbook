# Phase 01 — Product Discovery & Rapid Prototype

## Purpose

Turn a raw product idea into a coherent, interactive prototype that is good enough to evaluate the intended product and expose the questions that later engineering must resolve.

This phase is about **learning the product**, not designing its production architecture.

> Base44 should optimize for learning the product, not for pretending the product is production-ready.

The Guide LLM defined in [`../MASTER.md`](../MASTER.md) guides, analyzes, reviews, and advises throughout this phase. It does not implement the application itself. Rapid prototyping is performed through Base44 or a comparable prototyping tool.

## Phase boundary

The target progression is:

```text
RAW IDEA
→ PRODUCT DISCOVERY
→ PROTOTYPE BRIEF
→ RAPID PROTOTYPE
→ REVIEW & ITERATION
→ PROTOTYPE CANDIDATE
→ PROTOTYPE HANDOFF
→ PHASE 02 — FRONTEND PRODUCT DEFINITION
```

A prototype is evidence of product intent. It is not an architectural specification.

---

## 1. Entry criteria

This phase can begin from a very rough idea. The minimum useful starting context is:

- the product idea
- who might use it
- what problem, need, or experience it addresses

The user does not need to know these precisely in advance. When they are unclear, the Guide LLM should help discover them through focused questions.

The following are **not** required before this phase begins:

- technology stack
- database choice
- API design
- backend architecture
- authentication implementation
- hosting or deployment architecture
- detailed data model

Do not force premature technical decisions merely to make the prototype feel more complete.

---

## 2. Product discovery

Before opening Base44, conduct a short product-discovery conversation.

The purpose is not to create a complete PRD or resolve every business rule. It is to understand enough of the product to prototype it intentionally.

The discovery output should cover six areas.

### Product intent

What are we building, and why should it exist?

### Primary users

Who are the important actors or user groups?

### Core journeys

What are the most important things those users should be able to experience or accomplish?

### Initial scope

What needs to exist in the prototype for those journeys to be meaningfully evaluated?

### Out of scope

What are we intentionally not exploring or implementing during this phase?

### Open questions

What important questions have we discovered but deliberately left unresolved for later formal product definition?

Open questions are a valid output of this phase. Do not attempt to resolve every ambiguity through additional vibe coding.

The intended relationship is:

```text
Prototype discovers the question
            ↓
Phase 02 formalizes the decision
```

### Decision labels

The Guide LLM should distinguish clearly between:

- **User decision** — the user explicitly wants this.
- **Guide recommendation** — the Guide recommends this and explains why.
- **Provisional assumption** — acceptable for prototype progress, but intentionally subject to review in Phase 02.

Do not allow a Guide recommendation or prototype assumption to silently become a permanent product requirement.

---

## 3. Prototype brief

Before the first substantial Base44 generation, turn the discovery output into a concise Prototype Brief.

The brief should contain:

- product
- primary users
- prototype goal
- core journeys
- initial route/page map
- explicitly out-of-scope capabilities
- important UX constraints
- provisional prototype assumptions

The Prototype Brief is the working reference for Base44 iterations. It is not the final product specification.

---

## 4. Base44 strategy

### 4.1 Start with the product skeleton

Do not begin with a mega-prompt asking Base44 to build a complete production-ready application.

The first meaningful generation should establish enough structure to see and navigate the product:

```text
Visual direction / design language
        ↓
Global layout
        ↓
Navigation
        ↓
Route structure
        ↓
Representative pages
```

The objective is to make the product tangible quickly, not to perfect individual screens or encode final business rules.

### 4.2 Develop journey by journey

After the skeleton exists, iterate around user journeys rather than polishing isolated pages in random order.

A typical progression may resemble:

```text
Public discovery
      ↓
Core product journey
      ↓
Customer/user area
      ↓
Staff/admin experience
```

The actual journeys come from the Prototype Brief.

Prefer broad product coverage before deep visual polishing of one route.

### 4.3 Use a mock-first approach

The default for this phase is a frontend prototype backed by realistic mock or dummy data.

Do not build a production backend merely because the prototyping platform can generate one.

Mock data should support product evaluation, not merely fill empty cards. Prefer representative scenarios that expose meaningful states and journeys.

Examples may include different content states, appointments, customers, records, or requests where those concepts belong to the product.

The mock structures are prototype artifacts. They are not automatically the future backend schema.

### 4.4 Prototype meaningful behavior

The prototype should be more than a collection of static screenshots.

Core journeys should be interactively evaluable where useful, including behaviors such as:

- navigation
- selection
- filtering
- searching
- submission
- editing
- confirmation
- cancellation
- representative success states
- representative empty states
- basic failure states where they materially affect the experience

However:

```text
Prototype behavior ≠ production guarantee
```

A mock booking may demonstrate the intended user experience without proving concurrency safety. A simulated login may demonstrate identity-related UX without proving production authentication. Keep that distinction explicit.

### 4.5 Avoid prototype lock-in

When Base44 proposes generated backend capabilities, databases, authentication, platform functions, or other infrastructure, the Guide LLM should first ask whether they are necessary to learn the product during this phase.

If not, defer them.

During later engineering, preserve what the prototype taught us while re-evaluating implementation choices.

Generally preserve:

- product intent
- core journeys
- useful route/page coverage
- UX discoveries
- visual direction
- useful content
- representative scenarios
- product terminology
- known unresolved questions

Re-evaluate rather than automatically preserve:

- component architecture
- state management
- generated data structures
- mock API shape
- storage approach
- authentication simulation
- generated abstractions
- dependencies
- Base44-specific integrations

Never assume the prototype establishes:

- backend architecture
- database design
- security guarantees
- authorization guarantees
- concurrency guarantees
- production persistence
- production infrastructure

---

## 5. Review and iteration loop

After each meaningful Base44 iteration, pause and review before generating the next large change.

The working loop is:

```text
Base44 iteration
       ↓
User inspects the result
       ↓
Guide LLM reviews with the user
       ↓
What works?
What is missing?
What is premature?
What became inconsistent?
What did we learn about the product?
       ↓
Guide prepares the next scoped Base44 prompt
       ↓
Next iteration
```

Classify findings using four categories:

### KEEP

The result expresses the intended product well enough to preserve for the prototype.

### FIX NOW

The issue prevents meaningful evaluation of the current prototype or creates an important inconsistency that should be corrected before moving on.

### EXPLORE NEXT

The prototype has exposed an adjacent product area or journey worth exploring in the next iteration.

### DEFER TO PHASE 02

The question requires deliberate product definition rather than more vibe coding.

The Guide LLM should not praise every generated iteration automatically. Its job is to help decide what deserves another Base44 iteration and what should stop consuming prototype time.

---

## 6. Coverage before polish

Use this general priority:

```text
Coverage → Coherence → Behavior → Polish
```

Do not repeatedly perfect one landing page while important product journeys remain absent.

Once the intended prototype has sufficient coverage and coherence, perform a dedicated visual-consistency pass as appropriate. This may include:

- typography
- spacing and rhythm
- cards and surfaces
- button and CTA hierarchy
- responsive behavior
- visual hierarchy
- empty-state presentation
- consistency across related routes

Visual polish serves product evaluation. It is not a substitute for missing journeys.

---

## 7. Prototype completion review

Vibe coding must have an explicit stopping point.

Evaluate the prototype across three dimensions.

### Coverage

Are the core journeys and important pages identified in the Prototype Brief represented well enough to experience and evaluate?

### Coherence

Does the prototype behave and present itself as one product rather than disconnected generated screens? Consider navigation, content, mock scenarios, responsive behavior, and visual language.

### Learning

Has the prototype exposed enough of the product that remaining uncertainty is better handled through formal product definition than through additional Base44 prompts?

### Completion condition

The prototype is complete when it is sufficiently coherent and interactive to evaluate the intended product, core journeys are represented, major UX gaps are visible, and remaining uncertainty is better resolved through formal product definition than further vibe coding.

Prototype completion does **not** mean production readiness.

---

## 8. Prototype handoff

When the prototype meets the completion condition, stop casual expansion through Base44 and prepare it for the engineering workflow.

The transition should normally look like:

```text
Base44 prototype
      ↓
Export / repository / local environment
      ↓
Verify the project runs
      ↓
Preserve a usable prototype baseline
      ↓
Make the prototype accessible to engineering agents
      ↓
Record the Prototype Handoff
      ↓
Phase 02 — Frontend Product Definition
```

Do **not** make the first engineering instruction:

> Make this production-ready.

Do not immediately refactor the entire generated project either. First preserve and understand the prototype as the starting evidence for Phase 02.

### Prototype Handoff artifact

Create a concise handoff containing:

- project name
- prototype location/repository
- product intent
- primary users
- implemented journeys
- implemented routes/pages
- important prototype assumptions
- known limitations
- open product questions
- Base44/platform-specific dependencies
- intentionally deferred capabilities
- prototype completion status

This artifact is not the frontend specification. It tells the next phase what was built, what was learned, and what remains undecided.

---

## 9. Guide LLM responsibilities in this phase

The Guide LLM should:

- help turn a raw idea into a prototypeable product scope
- distinguish user decisions, recommendations, and provisional assumptions
- help prepare scoped Base44 prompts
- review important Base44 outputs with the user
- protect the prototype from premature backend/architecture work
- identify missing journeys and inconsistencies
- prevent endless visual iteration
- identify questions that belong in Phase 02
- help determine when the prototype has served its purpose
- help prepare the Prototype Handoff

The Guide LLM should **not**:

- implement the application itself
- treat Base44 output as final architecture
- design the production backend during this phase
- silently turn assumptions into requirements
- insist on resolving every product rule before prototyping
- encourage endless vibe-coding after the completion condition is met

---

## 10. Exit criteria

Phase 01 is complete when all of the following are true:

- product intent and primary users are sufficiently understood for the prototype
- core journeys and prototype scope are recorded
- a coherent interactive prototype exists
- important prototype assumptions are distinguishable from settled user decisions
- known open product questions are recorded rather than hidden
- the prototype has sufficient coverage, coherence, and learning value
- the prototype can be run/accessed by the next engineering workflow
- the Prototype Handoff exists
- the user agrees that further uncertainty should now be handled through formal frontend product definition rather than continued vibe coding

When these conditions are met, the Guide LLM should explicitly recommend ending Phase 01.

---

## 11. Transition to Phase 02

Phase 02 is **Frontend Product Definition**.

Its job is not to blindly polish or refactor the Base44 implementation. It will inspect the prototype, surface implicit and unresolved product behavior, and convert that behavior into explicit decisions before frontend engineering proceeds.

The governing document will be:

[`02-frontend-product-definition.md`](02-frontend-product-definition.md)

Do not invent Phase 02 procedure from this document. Follow its dedicated guide once that guide has been deliberately designed and approved.
