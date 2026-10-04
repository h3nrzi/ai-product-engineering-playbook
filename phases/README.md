# Workflow Phases

The playbook now uses three authoritative phases.

1. [`01-product-discovery.md`](01-product-discovery.md) — choose the product/model, discover the product, define its Product Delivery Phases, decompose the active delivery phase into modules, and finish with the authoritative PRD.
2. [`02-module-engineering.md`](02-module-engineering.md) — engineer one PRD module at a time using the Matt Pocock / AI Hero methodology, adapting the amount of process to the size of the module.
3. [`03-visual-redesign.md`](03-visual-redesign.md) — when needed, use Google Stitch to redesign and polish the completed product without changing approved product behavior.

```text
PRODUCT DISCOVERY + PRD
        ↓
MODULE-BY-MODULE ENGINEERING
        ↓
VISUAL REDESIGN / POLISH (IF NEEDED)
```

## Product Delivery Phases are separate

A product may have its own phased roadmap inside the PRD, for example:

```text
Delivery Phase 1 — Core MVP
Delivery Phase 2 — Operations expansion
Delivery Phase 3 — Growth features
```

These are not playbook phases.

During Phase 01, define the product roadmap and fully decompose only the active delivery phase into implementation modules. Future delivery phases remain high-level until they become active.

## Workflow principle

Product questions are resolved in Phase 01.

Architecture and implementation questions are resolved later, module by module, when they become relevant.

Visual redesign happens after functional coherence exists, not before.
