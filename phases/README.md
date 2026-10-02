# Workflow Phases

The playbook has five phases:

1. [`01-product-discovery.md`](01-product-discovery.md) — professional product discovery/design; produce the PRD and Base44 prompt package.
2. [`02-base44-prototype.md`](02-base44-prototype.md) — generate and refine the product prototype in Base44 and export a usable React baseline.
3. [`03-react-frontend-completion.md`](03-react-frontend-completion.md) — complete the Base44 React frontend with Matt Pocock-style Wayfinder → to-spec → to-tickets → implementation.
4. [`04-react-to-nextjs.md`](04-react-to-nextjs.md) — refactor the completed React app into Next.js using the same structured methodology.
5. [`05-fullstack-nextjs.md`](05-fullstack-nextjs.md) — replace mock/prototype boundaries with real server-side behavior and finish the integrated full-stack Next.js product.

```text
PRODUCT DISCOVERY
      ↓
BASE44 PROTOTYPE
      ↓
COMPLETE REACT FRONTEND
      ↓
REACT → NEXT.JS
      ↓
FULL-STACK NEXT.JS
```

Phase 01 carries most product-design/discovery depth. Phases 03–05 use a deliberately repeatable and lightweight engineering loop rather than accumulating additional workflow ceremony.
