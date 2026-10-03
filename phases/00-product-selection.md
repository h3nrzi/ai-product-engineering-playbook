# Pre-Phase 00 — Product Family & Model Selection

## Purpose

Select **what kind of service product** will enter Phase 01 before doing product discovery.

This pre-phase exists because one broad service family can contain materially different products.

Example:

```text
Barbershop / Beauty Salon Booking
├── Men’s single barbershop
├── Women’s single salon
├── Unisex salon
├── Independent specialist / studio
├── Multi-branch salon
├── Multi-salon marketplace
└── At-home beauty service
```

A marketplace, fixed-location salon, and at-home service may share a domain while having different actors, workflows, trust models, logistics, operations, and monetization. Do not ask Phase 01 to discover which business model the user meant when that choice can be made explicitly first.

## Canonical sources

- Product catalog: [`../opportunities/service-products.md`](../opportunities/service-products.md)
- Selected Opportunity Brief template: [`../templates/selected-opportunity-brief.md`](../templates/selected-opportunity-brief.md)

## Step 1 — Select Product Family

Choose one service by name from the opportunity list.

Consider:

- approximate demand in Iran;
- problem strength;
- workflow depth;
- portfolio differentiation;
- overlap with active/completed projects.

The list gives an approximate order, not a project-selection score.

## Step 2 — Select Product Model / Variant

Resolve the materially different model before Phase 01.

Model dimensions can include:

- single provider vs chain vs marketplace;
- fixed-location vs at-home/mobile vs remote;
- consumer vs B2B;
- instant booking vs request-to-book vs quote-first vs dispatch;
- one-time vs subscription/recurring vs packages/credits;
- general audience vs a meaningful vertical/audience specialization.

The selected model should be specific enough that its primary actors and service-delivery structure are understandable, but it should **not** prematurely define detailed features.

## Step 3 — Record Adjacent Models Explicitly Out of Scope

Write down the closest variants that are not part of this project.

This prevents scope drift such as:

```text
single salon
→ quietly becomes multi-branch
→ quietly becomes marketplace
→ quietly requires marketplace payouts/moderation/provider onboarding
```

A model can change later, but only as a deliberate product decision.

## Step 4 — Persist Selected Opportunity Brief

Create:

`projects/<project-slug>/selected-opportunity-brief.md`

It must record at least:

- family name;
- selected Model / Variant;
- target market/geography when relevant;
- target users at a high level;
- primary problem at a high level;
- proposed solution direction;
- why the opportunity is worth exploring;
- explicit model boundaries.

## Step 5 — Create / Update Tracker

The project tracker must record the same Product Family + Model and link the brief.

## Completion gate

Pre-Phase 00 is complete only when:

- one Product Family is selected;
- one sufficiently specific Product Model / Variant is selected;
- adjacent models are explicitly bounded out;
- the Selected Opportunity Brief is persisted;
- the tracker records the same selection;
- no unresolved model choice would materially change the actors or core service workflow.

Then proceed to **Phase 01 — Product Discovery & Product Design**.
