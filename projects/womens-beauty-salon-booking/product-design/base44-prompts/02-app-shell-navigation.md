# Prompt 02 — App Shell & Navigation

## Objective

Build the reusable application shells and navigation structure for the approved **single-location women’s beauty salon booking product**.

This step should establish how users move between public discovery, customer account, salon operations and manager-only controls while preserving the role/access boundaries already defined in the product design.

Do **not** finish the public discovery pages, booking/payment flow, customer appointment workflows, salon operations logic or manager forms in this step. Build the shells, navigation, access-aware structure and placeholder destinations needed by later prompts.

Preserve all work from Prompt 00 and Prompt 01. Do not replace the approved design system or global fixtures.

## Approved product areas

The product has four structural areas:

1. Public discovery and booking entry.
2. Authenticated customer account.
3. Salon operations for reception and managers.
4. Manager-only controls inside the same salon operations area.

There is no specialist dashboard, branch selector, marketplace vendor area, multi-salon switcher or separate admin product.

## Public application shell

Create a Persian/RTL public shell using the approved design system.

Primary navigation destinations:

- `خدمات`
- `متخصص‌ها`
- `درباره سالن و تماس`
- `نوبت‌های من`

Also provide:

- a temporary replaceable salon identity using the existing demo label `سالن نمونه`,
- salon identity/logo area returning to Home,
- a visually prominent `رزرو نوبت` primary action,
- footer access to essential general salon/contact and booking-policy context without inventing new legal or marketing pages.

Do not add a standalone Login item to the primary navigation. Authentication is an access step when a customer enters a private surface or reaches the approved booking stage.

### Public navigation behavior

- Home/logo returns to the public home surface.
- `خدمات` opens the services area.
- `متخصص‌ها` opens the specialists area.
- `درباره سالن و تماس` is one grouped destination; do not split it into two thin main-navigation pages.
- `نوبت‌های من` remains visible while signed out. If authentication is needed, simulate login and return to the originally intended account destination afterward.
- `رزرو نوبت` begins the booking journey without requiring a detour through unrelated pages.
- Public service and specialist destinations will cross-link later; prepare routing/navigation structure for those links without building their full content now.

Do not expose private appointment information in public navigation, previews or unauthenticated deep-link placeholders.

## Public responsive shell

On narrow screens:

- use a compact header,
- keep the booking action clearly available,
- use a labeled menu/drawer for the approved navigation destinations,
- keep `نوبت‌های من` discoverable,
- do not replace all navigation with unlabeled icons,
- do not stack a persistent navigation bar in a way that will conflict with later sticky booking actions.

On wider screens:

- show primary navigation directly when space allows,
- retain the prominent booking action,
- keep active destination styling visible and text-based.

Menu overlays must be keyboard operable, trap/manage focus appropriately, and return focus to the opener when closed.

## Customer account shell

Create a distinct authenticated customer-area shell while preserving the same product identity and visual language.

Customer account navigation contains only:

- `نوبت‌های من`
- `اطلاعات من`

Also provide a clear sign-out account control.

Do not add:

- wallet,
- loyalty,
- notifications inbox,
- saved specialists/favorites,
- payment-method management,
- separate messages/chat,
- account ownership-transfer editor.

### Customer access behavior

Use the simulated customer authentication context from Prompt 00.

- Signed-out access to an account destination should lead through the simulated mobile/SMS access step and then return to the intended destination.
- Private account destinations belong only to the original owning customer context.
- A different appointment contact must not be treated as another account owner.
- Sign-out should clear private account presentation and return to a safe public state.
- Direct links to private placeholders must enforce the same simulated ownership/access rule as normal navigation.

Do not build complete appointment lists/details or account support flows yet; those belong to Prompt 05.

## Salon staff access shell

Create the salon operations entry and access-aware shell for reception and manager contexts.

Staff access is separate from customer authentication.

Use the approved simulated pattern:

- mobile number,
- one-time SMS verification state,
- assigned-role check.

A phone that passes simulated SMS verification but has **no assigned staff role** must still be denied access to salon operations.

Never imply real authentication or real SMS verification.

### Operations default destination

After successful assigned-role access, the default salon operations destination is:

- `تقویم نوبت‌ها`

This is intentionally calendar-first.

## Reception navigation

Reception-visible operations navigation should provide:

- `تقویم نوبت‌ها`
- `پیگیری‌ها`

Also provide a clear persistent/contextual `نوبت جدید` action, but do not require it to be a permanent main-navigation page.

Appointment detail is contextual from the calendar/follow-up areas and should not be a separate top-level menu destination.

Do not add separate calendars for online, telephone, in-person or walk-in booking sources. They share one operational schedule truth.

Do not add accounting, CRM, analytics or reminder-system navigation.

## Manager navigation

Managers inherit the full reception shell and additionally see manager-only destinations:

- `خدمات`
- `متخصص‌ها`
- `برنامه کاری`
- `تنظیمات رزرو`
- `دسترسی کارکنان`

These controls live inside the same salon operations product area rather than a separate admin application.

Manager exceptions, ownership-support review and similar sensitive actions remain contextual to the relevant appointment/account and are **not** standalone main-navigation destinations.

### Role boundary

Reception must not see or access manager-only controls.

Manager-only restrictions apply to:

- visible navigation,
- direct-route/deep-link access,
- contextual actions,
- placeholder management surfaces.

Do not merely hide menu labels while leaving unrestricted direct access.

For this prototype, enforcement may be simulated deterministically, but the UI should make the permission boundary clear and never claim production-grade authorization/security.

## Salon responsive shell

For desktop/tablet operations:

- use persistent side navigation where practical,
- show the current section clearly,
- keep `نوبت جدید` readily available,
- preserve enough content width for the later calendar and management forms.

For narrow screens:

- use a labeled menu/drawer,
- display the current section title,
- retain access to `نوبت جدید`,
- do not try to squeeze a desktop side navigation or full calendar grid into the viewport,
- keep all permitted destinations reachable rather than deleting functionality on mobile.

Do not create separate mobile and desktop products; adapt presentation while retaining the same hierarchy.

## Route / surface preparation

Prepare clean destinations or lightweight placeholders for the approved later surfaces without implementing their full contents yet.

Public placeholders:

- Home
- Services
- Service detail template
- Specialists
- Specialist profile template
- About salon and contact
- Booking/result container

Customer placeholders:

- My appointments and attempts
- Appointment/attempt detail
- My information

Salon operations placeholders:

- Staff sign-in
- Calendar/appointments
- Appointment detail
- Follow-up

Manager placeholders:

- Services management
- Specialists / eligibility / priority
- Working schedules / conflicts
- Booking settings
- Staff access / contextual support

The exact route structure is an implementation choice. Do not create unnecessary separate routes for every booking step, modal or state simply because placeholders are being prepared.

## Cross-area navigation rules

Prepare navigation so later prompts can implement these approved transitions:

- Service detail → eligible specialists or service booking, preserving selected service.
- Specialist profile → supported service booking, preserving named specialist preference.
- Booking result → owning customer appointment/attempt detail.
- Signed-out customer deep link → simulated customer login → intended private destination.
- Staff calendar/follow-up → exact staff appointment detail.
- Conflicting manager schedule item → affected appointment detail.
- Public/customer support context → salon contact without treating contact as ownership proof or policy exception.

Do not implement the full workflow behavior yet; preserve the structural destination and intended return context.

## Active states and orientation

Across every shell:

- show the current destination/section using label plus approved visual emphasis,
- do not rely on color alone,
- keep headings consistent with navigation terminology,
- distinguish customer account from salon staff operations,
- never show manager controls to a reception context,
- never expose prior-account private content after sign-out or context switching.

Avoid breadcrumbs where they add no useful orientation. Use them only if a later nested detail surface genuinely benefits.

## Visual and interaction rules

Use the approved Prompt 01 design system without creating another shell-specific visual language.

- Persian and RTL globally.
- Vazirmatn typography.
- Warm ivory canvas, white surfaces and deep-plum primary.
- Visible focus states.
- Minimum 44 px interaction target for navigation controls.
- Labeled actions rather than ambiguous icon-only navigation.
- Moderate radius and restrained elevation.
- Active navigation should remain readable at text zoom and with long Persian labels.
- Menu/drawer open/close behavior must preserve focus correctly.

Do not add decorative luxury-gold styling, glassmorphism, unrelated gradients or page-specific palettes.

## Content rules

Use the canonical Persian terms:

- `رزرو نوبت`
- `خدمات`
- `متخصص‌ها`
- `درباره سالن و تماس`
- `نوبت‌های من`
- `اطلاعات من`
- `تقویم نوبت‌ها`
- `پیگیری‌ها`
- `نوبت جدید`
- `برنامه کاری`
- `تنظیمات رزرو`
- `دسترسی کارکنان`

Keep temporary/demo labeling honest. Do not add marketing claims, fabricated review counts, credentials, or fake operational contact details.

## Do not add

Do not add during this shell/navigation step:

- full service/specialist discovery content,
- completed booking steps,
- real or simulated payment outcomes beyond placeholder navigation,
- detailed customer appointment management,
- full calendar interactions,
- management CRUD logic,
- dashboards/analytics,
- marketplace or branch navigation,
- specialist login/dashboard,
- chat/messages inbox,
- loyalty/wallet/favorites,
- accounting/POS/CRM/inventory/payroll sections,
- notifications center or reminders page.

Do not redesign Prompt 00 fixtures or Prompt 01 components unless a real contradiction prevents the shell from working.

## Acceptance check

Before considering this step complete, verify that:

- public navigation contains exactly the approved primary destinations plus the prominent booking action;
- `نوبت‌های من` is reachable while signed out and can return to its intended destination after simulated login;
- Login is not an unnecessary permanent public navigation item;
- customer account navigation contains `نوبت‌های من` and `اطلاعات من` plus sign-out, with no deferred account features;
- staff operations are clearly separate from customer account access;
- operations default to `تقویم نوبت‌ها`;
- reception sees calendar, follow-up and the new-appointment action but no manager controls;
- manager sees reception functionality plus services, specialists, working schedules, booking settings and staff access;
- a simulated verified number without an assigned staff role receives an access-denied state;
- direct/deep-link placeholders respect the same role boundaries as visible navigation;
- public/customer shells work cleanly on narrow screens and salon operations adapt to a labeled drawer rather than a squeezed desktop sidebar;
- focus behavior works for menus/drawers and active sections remain understandable without color alone;
- private customer/staff details are never exposed by public placeholders;
- no full page/business workflow from later prompts has been prematurely implemented or invented;
- no deferred feature or adjacent product model has been introduced.

Stop once shell structure, navigation, destination placeholders and access boundaries are coherent. The next prompt builds the public discovery surfaces inside this shell.