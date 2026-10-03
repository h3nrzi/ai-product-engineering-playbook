# UX States & Edge Cases — Women’s Beauty Salon Booking

## Status and authority

Stage 10 draft prepared on 2026-10-03 for review. Derived from [approved user flows](user-flows.md), [page/surface inventory](page-inventory.md), [information architecture](information-architecture.md), and [product scope](product-scope.md). State presentation and recovery proposals below preserve approved booking rights and rules; Stage 10 is not yet approved.

P/B/C identifiers refer to the surface inventory. These are states of existing surfaces, not new pages/routes. Numeric service configuration, provider behavior, verification security controls, and brand/visual details are not invented here.

## State principles

- Distinguish empty results, loading, a known failure, and an unknown operation outcome.
- Distinguish selected time from an actual held slot, payment success from confirmed appointment, and cancellation from completed refund.
- State messages name what happened, whether the appointment/time is still valid, and the next useful action.
- Preserve valid selections/input during recoverable errors. A changed dependency invalidates only what no longer fits.
- Show authoritative status after interruption; do not invite duplicate booking, payment, cancellation, or refund attempts.
- During a submitted operation, show progress and prevent repeat submission. A disabled control explains its reason.
- Never silently substitute a named specialist, rewrite accepted terms, extend deadlines, transfer ownership, or delay the next appointment to hide a failure.
- Private data/authorization is checked after login and for direct links. Cross-account switching/sign-out does not expose the prior customer's form or booking data.
- Use explicit text/icons along with color. Feedback, countdowns, and action controls must be readable and operable in Persian/RTL.
- Announce significant outcome/error changes accessibly; do not continually announce every timer tick.

## 1. Discovery, service selection, and availability

| Surface/state | Visible information | Actions and preserved context | Constraint / outcome |
| --- | --- | --- | --- |
| P02–P05 loading | Loading content indication, not fake zero results | Keep current service/filter/context | Do not label a service unavailable before loading resolves |
| P02 empty service list | «فعلاً خدمتی برای رزرو نمایش داده نمی‌شود» and salon contact | Contact salon; return home | No invented bookable service |
| P03 consultation required | Service information and explanation that consultation is needed | Contact salon | No direct payment/booking action |
| P03/P05 missing or no-longer-public entry | Clear unavailable information and valid public alternatives | Services/specialists/contact | Do not expose archived private data or keep an invalid booking choice |
| B02 volume unselected | Required service-relevant options and duration context | Choose one; keep service | No unnecessary volume step for fixed-duration service |
| B03 specialist unavailable/ineligible for service | Eligibility explained; invalid option not selectable | Customer chooses another specialist or any eligible | Priority never overrides eligibility |
| B04 loading/rechecking | «در حال بررسی زمان‌های آزاد» | Preserve service/volume/preference and date | No claimed hold |
| B04 no valid times | «برای این انتخاب در این تاریخ وقت آزاد نداریم» | Other date; customer-chosen specialist/any eligible; salon contact | Do not silently replace named preference or shorten duration |
| B04 selected | Selected slot distinguished visually/textually; booking duration visible | Continue/back | Selection is not reservation |
| B04/B06 stale time conflict | «این زمان دیگر آزاد نیست؛ زمان دیگری انتخاب کنید» | Preserve name/contact and valid service/volume/preference; refresh availability | Do not proceed to payment without a valid hold |
| B06 any-eligible assignment changed before hold | Show updated specialist explicitly in review | Review/accept by proceeding; go back | No hidden substitution |
| Discovery/availability read error | «دریافت اطلاعات ممکن نشد» instead of an empty-result message | Retry read; keep choices | Last-known availability is not proof the time is still bookable |

Price presentation labels an approximate basis wherever relevant and separates exact deposit from estimated total/balance. An image failure uses a neutral fallback while retaining useful text/actions; it does not make an otherwise bookable service unavailable.

## 2. Customer and staff authentication, contacts, and access

| Surface/state | Visible information | Recovery/preservation | Access constraint |
| --- | --- | --- | --- |
| C01 mobile validation | Field-specific error with required format | Correct value; retain booking selections | Do not request an SMS to an invalid number |
| C01 code being sent | Sending indication and target number | Wait; prevent duplicate submit | Sending is not verification |
| C01 code invalid/expired | Clear error for the code | Correct/retry; resend when permitted; preserve booking choices | No account/contact verification on error |
| C01 resend temporarily unavailable | Explain waiting and available retry timing | Keep current step; allow correcting mobile | Security resend/attempt limits come from engineering, not indefinite UI spinning |
| C01 contact vs login check | Show exactly which number and purpose is being verified | Changing contact invalidates verification for that choice | Contact check stays in original account |
| Customer session expired | Ask for login and explain that time will be rechecked | Preserve non-sensitive selections where practical; return to intended owned surface | Login itself does not hold or extend a slot |
| P11 valid number but no staff role | «دسترسی به پنل سالن برای این شماره فعال نیست» | Contact manager; change account | Mobile verification alone does not grant operations access |
| Private direct link owned by another account | Explain access is unavailable without exposing details | Sign in with appropriate account; salon contact | Link/reference alone never grants ownership |
| Reception attempts manager action | Control absent/unavailable with concise permission explanation | Route issue to management | No frontend navigation shortcut bypasses role checks |
| C09 insufficient ownership evidence | Pending verification or access-transfer denied, clearly distinguished | Manager support follow-up | No ownership change while unresolved |
| Auth/read service unavailable | Recovery message and retry | Preserve permitted input; do not disclose private details | Existing payment/hold keeps its actual deadline |

Draft selections may survive interrupted login on the same device where practical. Do not promise cross-device persistence of unsubmitted input. Payment attempts and authoritative booking/refund outcomes remain retrievable in the original owning account.

## 3. Review, hold, payment, and result

| State | Customer sees | Allowed next action | Calendar/payment meaning |
| --- | --- | --- | --- |
| Final review ready | Actual specialist, duration/time, exact deposit, price basis, accepted rules | Pay deposit; edit valid choices | No hold until slot successfully secured |
| Securing hold / creating payment | Progress and disabled repeat Pay action | Wait; on unknown result check attempt status | Do not create competing duplicate attempts |
| Hold could not be secured | Selected slot conflict message | Return to availability with valid input preserved | No deposit invitation for unowned slot |
| Hold active, payment not started | Actual expiry and remaining time | Proceed to payment, or explicitly abandon unpaid hold before editing | Same specialist/time blocked until release/expiry |
| Abandon unpaid held selection | Explain release before changing choice | Deliberate release and return to selection | No deadline reset from back navigation alone |
| Payment initiated/result unknown, still held | «در حال بررسی پرداخت هستیم», actual verification deadline, whether slot remains held | Check status; wait; salon contact | Do not invite repeat payment or move this attempt to another slot |
| Definitive payment failure | «پرداخت انجام نشد؛ نوبت تأیید نشده» | Check availability and pay through a new valid attempt | Hold released; no confirmed booking |
| No payment started by hold expiry | «زمان رزرو آزاد شد» | New selection from current availability | Unconfirmed/expired attempt |
| Still unknown at final verification deadline | Slot released message plus separate ongoing payment verification | Check existing payment status; salon contact | No confirmed booking; uncertainty remains tracked |
| Verified success while held | «نوبت شما تأیید شد» plus reviewed details and deposit | View appointment | Same reviewed specialist/time confirmed |
| Success verified after release | «پرداخت دریافت شد، اما نوبت تأیید نشد؛ بیعانه کامل بازگردانده می‌شود» | Refund status; optional new booking | Never auto-confirm, even if original slot is now free |
| Payment status check unavailable | Last known result and «بررسی دوباره وضعیت» | Retry status read; salon contact | Network error is not definitive failure or deadline extension |
| Result screen closed/reopened | Current account-linked attempt/booking/payment/refund result | Relevant current action | Authoritative outcome is not lost by closing the page |

Initial timing remains 10 minutes from hold creation plus up to 5 additional minutes only for payment started in time with unknown result. Display both the actual ordinary deadline and the final verification deadline when applicable. Browsing, login, reopening a link, and status checking do not extend either.

Payment-provider return text or customer screenshots alone must not be presented as verified success. Exact verification operations belong to engineering.

## 4. Customer appointment list and changes

| Surface/state | Information and actions | Preservation/recovery | Result boundary |
| --- | --- | --- | --- |
| P08 no appointments | «هنوز نوبتی ثبت نکرده‌اید» and booking action | Start booking | Different from a failed data load |
| P08 no upcoming appointments but prior attempts/history | Clear groups and current pending/refund attention | Open past/attempt details | Do not hide unconfirmed payments or refunds |
| P08/P09 read error | Retry message | Keep intended owned appointment context | Do not falsely show no appointments |
| P09 confirmed | Details, stored cutoff/terms and only permitted actions | Relevant change/cancel/contact | State drives actions |
| C03 within stored cutoff | Original booking plus valid new-time choices | Back abandons uncommitted selection | Original held until replacement succeeds |
| C03 replacement conflict/failure | Explain failure/new choice | Preserve original appointment/deposit; keep valid new-choice intent | No partial move or second deposit |
| C03 cutoff passes while screen is open | Explain online rescheduling now unavailable | Keep original; contact salon for manager exception | Recheck deadline at application |
| C04 cancellation review | Exact booking, full/no-refund consequence | Cancel action or keep appointment | No silent destructive action |
| C03/C04 submitting | Processing, repeat action disabled | Wait/check actual status if interrupted | No blind duplicate mutation |
| C03/C04 outcome unknown | «وضعیت تغییر را بررسی می‌کنیم» and current-status check | Read authoritative appointment before retry | Do not label known success/failure prematurely |
| P09 cancelled | Cancellation state plus independent refund status | Track refund/contact; optional new booking | Cancellation is not completed refund |
| P09 completed/no-show | Actual recorded outcome and payment information | View details/contact | No customer editing of past booking |

A customer action completed at or before the stored cutoff qualifies. After the cutoff, online rescheduling is unavailable; cancellation can still show its disclosed no-refund consequence. Late exceptions require manager approval with a reason. Rescheduling keeps original accepted terms; review shows the recalculated deadline even when it has already passed.

## 5. Reception booking, receipts, and salon changes

| Surface/state | Staff/customer information | Actions / preservation | Rule |
| --- | --- | --- | --- |
| C02 incomplete intake | Field-specific missing name/contact/service/time | Correct only missing input | No repeated profile data or assumed verified customer |
| C02 conflict while entering | Current slot unavailable | Keep intake; choose valid alternative | Shared online/reception availability |
| C02 finalized link-booking | Hold expiry, SMS sending/delivery, deposit state | Send/retry valid link; view current result | Hold starts on finalize/link-send request |
| C11 SMS failure within hold | Failed communication shown separately | Retry same valid link; contact customer | No new booking or reset deadline |
| C11 link expired | Expired link/attempt | Fresh availability/review for new attempt | Reopening does not revive hold |
| C07 in-salon deposit not received | Actual receipt still required | Record only after receiving amount/source | No assertion that uncertain online payment was received |
| Immediate walk-in unavailable | No full-duration immediate slot | Offer customer-chosen valid alternative | Later visit uses future-deposit path |
| C05 proposal awaiting response, original deliverable | Original still confirmed, proposal separately visible | Customer Accept/Decline; staff follow-up | No silent replacement; no reply is not consent |
| C05 original undeliverable | Salon cancellation/refund entitlement, optional proposal | Explicit customer-chosen replacement/new path | Cancellation/refund cannot wait indefinitely for a reply |
| C05 accepted alternative now conflicts | Explain conflict | Keep deliverable original; find/review another valid alternative | Acceptance cannot bypass availability |
| C06 manager exception lacks reason | Required reason error | Add reason or abandon | Reception cannot authorize exception |
| C08 inaccurate volume at salon | Fixed booked start/duration and coordination outcome | Specialist resolves within interval | No extension or next-appointment delay |
| C08 no in-slot solution | Full-refund cancellation and optional new booking | Customer chooses whether to book again | Not automatically a late-customer forfeiture |
| C07 final-price disagreement | Service has not begun; explain salon coordination | Coordinate specialist/customer; apply applicable approved rule or manager exception | No automatic charge or time change |
| C07 receipt save failed/unknown | Receipt recording state clearly uncertain | Check saved state before retry | Actual receipt and persisted record are distinct |

Notify appointment changes/cancellations by SMS and show actual result in the account. Failed delivery never reverses an otherwise successful booking change. Staff follow-up surfaces link to the exact appointment/attempt rather than inventing a reminder system.

## 6. Management, schedule conflicts, and refunds

| Surface/state | Information and action | Preservation/recovery | Boundary |
| --- | --- | --- | --- |
| P15/P16 missing required configuration | Field-specific price/duration/eligibility/label errors | Correct; keep unsaved valid input | Do not publish invalid bookable combinations |
| P18 invalid settings | Positive price/hold/duration, deposit >0 and <=100, cancellation window >=0 as applicable | Correct values before saving | Defaults remain 20%, 24 hours, 10-minute hold |
| C12 affected confirmed bookings/holds | List conflicts and link to details | Resolve under consent/full-refund rules before conflicting save | No silent invalidation/reassignment of holds or accepted bookings |
| Management save processing | Saving status and repeat submission disabled | Wait/check published values if unknown | No claim of publication on button click alone |
| Management save failed | Error with retained unsaved values | Retry valid save or discard | Previous published settings remain |
| Management stale edit | Current values changed since editing, relevant differences | Reload/review changes before save | Do not silently overwrite another staff action |
| C09 recovery verification incomplete | Pending/denied request with reason and next support step | Keep request without applying transfer | Login/contact editing does not bypass ownership |
| Refund due/pending | Entitlement, exact amount, source and actual available timing | View/check progress; staff processing | No instant-refund claim or forced credit |
| Refund processing needs attention | Entitlement remains with staff follow-up and customer contact | Check actual refund state; retry only safely | Failed refund does not erase entitlement |
| Refund completed | Verified/documented return with amount/reference/time | View record | Cancellation or sending a refund request alone is not completion |

Deposit calculation is rounded once to the nearest whole toman, half upward, and saved as the exact payable amount. A provider-unit conversion must preserve it. Later setting changes affect new bookings only.

## 7. Responsive, content, and accessibility edge cases

- Small screens: maintain readable summaries, labels and primary actions; steps may scroll without hiding the actual reviewed specialist/time or payment consequence.
- Persian/RTL: use consistent date/time/currency formatting; phone/code fields remain readable and unambiguous. Detailed typography/format standards follow later content/design stages.
- Long service/specialist names and policy text wrap; do not truncate essential appointment identity or refund consequences.
- Missing optional profile/image fields use a clear fallback; missing required booking name/contact asks only for those fields.
- No color-only status, errors, selected slot, or permission cues. Provide readable text, visible focus, associated field errors and keyboard/touch-operable actions.
- Busy/disabled actions explain processing or unavailable conditions. Move focus to actionable error summaries or confirmed outcomes appropriately; do not trap users in a dialog.
- Interrupted connection distinguishes unsent input from an operation with an unknown outcome. Keep input; read current state before repeating a possibly committed operation.
- Sign-out/account switch removes private prior-account details. A denied link gives no appointment information.
- Date/time changes near midnight or a cutoff use actual appointment/deadline information, not a device countdown alone. A past time is not offered as a valid new booking.
- Back navigation and reload preserve valid intent where practical while showing current authoritative state for an existing attempt; no promise of unsubmitted cross-device persistence.

## Prototype demonstration and review checks

Base44 may simulate these conditions. The prototype should demonstrate meaningful recovery on the existing surfaces:

1. No valid time vs availability-loading error: different messages and useful actions.
2. Login/contact-code error preserves service, volume, specialist preference and time; recheck availability afterwards.
3. Slot lost before payment: no charge invitation, valid input retained and return to time selection.
4. Pending payment: held vs released states are explicit; no duplicate payment action while uncertainty remains.
5. Late verified success: no booking confirmation, separate full-refund progress.
6. Failed reschedule: original time/deposit intact; cancellation does not claim completed refund.
7. Unanswered proposal: deliverable original preserved; undeliverable original cancelled with full refund.
8. Failed SMS: same booking result remains; resend does not restart deadline.
9. Reception denied manager exception/settings action; ownership recovery remains pending/denied until verified.
10. Volume mismatch: booked interval unchanged; no solution uses full-refund cancellation and customer-chosen new booking.
11. Invalid/conflicting/stale management edit: old published values/accepted bookings preserved.
12. Empty account vs failed account read and unconfirmed-attempt/refund retrieval remain distinct.

These are product/prototype acceptance scenarios, not a claim of implemented or tested server guarantees.

## Completion condition

State feedback, permitted actions, preserved context and recovery for critical surfaces are defined without adding pages or changing approved customer rights. Review this draft as a whole; Stage 10 remains in progress until user approval. Next is Stage 11 — Brand & Visual Direction.
