# Project Tracker — Women’s Beauty Salon Booking

> Operational control panel for the project. Product behavior belongs in the PRD; this tracker only shows where the project is, what is authoritative, and what should happen next.

## 1. Project Snapshot

| Field | Value |
| --- | --- |
| Product family | Barbershop / Beauty Salon Booking ([catalog](../opportunities/service-products.md)) |
| Selected model / variant | **Women’s single-salon** |
| Target market / geography | Persian-language product for the Iranian market |
| Current playbook phase | **01 — Product Discovery & Delivery Plan** |
| Current product delivery phase | Not defined yet |
| Current module | None |
| Overall status | **active** |
| PRD | Pending — [`womens-beauty-salon-booking/prd.md`](womens-beauty-salon-booking/prd.md) |
| Implementation repository | Pending |
| Documentation root | [`projects/womens-beauty-salon-booking/`](womens-beauty-salon-booking/) |

### Product boundary

- **Selected:** one physical women’s beauty salon.
- **Explicitly not:** men’s barbershop, unisex salon, independent-specialist marketplace, multi-salon marketplace, multi-branch salon network, or beauty-at-home/mobile workforce product.

A deliberate model change must update the PRD and this tracker before work continues.

---

## 2. Playbook Progress

| Playbook Phase | Status | Exit Result |
| --- | --- | --- |
| 01 — Product Discovery & Delivery Plan | **active** | Authoritative phased PRD + active-phase module map |
| 02 — Module-by-Module Engineering | not started | Reviewed working modules / completed product delivery phases |
| 03 — Visual Redesign & UI Polish | not started | Final Stitch-driven visual redesign/polish when needed |

---

## 3. Product Delivery Roadmap

Not defined yet.

The product discussion must determine how many delivery phases the product needs and what each phase is meant to achieve. Future phases should remain high-level; only the active delivery phase will be decomposed into detailed modules.

### Active delivery phase

- **Phase:** Not defined
- **Objective:** Pending product roadmap decision
- **Exit condition:** Pending product roadmap decision

---

## 4. Module Board

No modules are defined yet.

Module decomposition starts only after Product Delivery Phase 1 has a clear goal and boundary.

---

## 5. Current Focus

- **Current module:** None
- **Current activity:** Product delivery planning
- **Immediate objective:** Define the product delivery roadmap and the exact boundary of Product Delivery Phase 1
- **Working artifact:** This tracker until `prd.md` is created

### Open decisions

| Decision | Owner | Needed For | Status |
| --- | --- | --- | --- |
| How many Product Delivery Phases should this product have? | User + Guide | Product roadmap | open |
| What must Product Delivery Phase 1 make usable? | User + Guide | Phase 1 boundary and module map | open |

---

## 6. Risks & Blockers

None.

The project is intentionally paused before module decomposition until the delivery roadmap is agreed.

---

## 7. Authority & Artifacts

| Artifact | Role | Location |
| --- | --- | --- |
| PRD | Product authority | Pending — `projects/womens-beauty-salon-booking/prd.md` |
| Active module artifact | Current engineering authority | Not applicable yet |
| Implementation repository | Source code and engineering evidence | Pending |
| Visual redesign artifact | UI authority if Phase 03 is used | Pending |
| Project workspace | Minimal project context | [`womens-beauty-salon-booking/README.md`](womens-beauty-salon-booking/README.md) |

---

## 8. Next Action

> **Define the Product Delivery Phases and agree the exact goal/boundary of Product Delivery Phase 1.**

After that, decompose Phase 1 into coherent product modules and write the authoritative PRD.

---

## 9. Session Handoff

- **Where we are:** Playbook Phase 01, before Product Delivery Roadmap definition.
- **What is settled:** Product family/model is Women’s single-salon for the Iranian/Persian market; adjacent salon models are excluded.
- **What is happening now:** Deciding how the product should be delivered in product-specific phases.
- **What happens next:** Define the Product Delivery Phases and Phase 1 boundary, then derive the module map.

### Guide entrypoint

Read in this order:

1. [`MASTER.md`](../MASTER.md)
2. this tracker
3. [`phases/01-product-discovery.md`](../phases/01-product-discovery.md)
4. [`womens-beauty-salon-booking/README.md`](womens-beauty-salon-booking/README.md)

Continue from the Product Delivery Roadmap decision. Do not restart project selection or invent module boundaries before Phase 1 is defined.