# Proposed App Changes — Haulier Access to Agg Loads

**App:** Meaney App
**Purpose:** Let subcontracted haulage drivers raise agg load dockets without the office creating an account
for each driver.

---

## 1. The problem today

Every person who does dockets needs a profile in the app. Haulage drivers turn over constantly — agency
drivers, different lorries, different companies week to week — so the office ends up creating, chasing and
resetting accounts for people who might do three loads and never come back. In practice that means dockets
don't get done in the app at all.

**Client's words:**

> "Is there a way that each driver doesn't have to have a profile and basically they add their company and
> name and away they go to be able to do dockets?"

## 2. The proposed solution in one line

Add a third sign-in type — **Haulier** — that takes no credentials: the driver picks their haulage company
from Meaney's approved list, types their name and vehicle reg, and lands straight on Agg Loads to do dockets.

---

## 3. Who gets access

| Login type | Who | Credentials |
|---|---|---|
| Employee (existing) | Meaney staff | Password |
| Subcontractor (existing) | Subcontract crews | Password |
| **Haulier (new)** | Subcontracted haulage drivers | **None** |

The **company** is approved once by Meaney. Individual drivers are never set up.

## 4. What the driver does

1. Taps **Haulier** on the Sign In screen.
2. Picks their **haulage company** from a dropdown of hauliers Meaney has approved.
3. Types **driver name** and **vehicle reg**. Mobile optional.
4. Taps **Start doing dockets** — straight onto Active Loads.

The device remembers them. From the next day, tapping **Haulier** goes straight to Active Loads and the entry
screen never appears again.

**Company is a dropdown, not free text.** This is the one field that must be constrained: free text gives you
"Byrnes", "Byrne Haulage" and "byrne haulage ltd" as three different suppliers inside a week, and then
dockets can't be matched to a supplier account for self-billing.

**Company not on the list** → a short request-access screen (company, contact, mobile, number of lorries)
that goes to the Meaney office. Approving the company is the only gate in the whole flow.

## 5. What a haulier sees

Lands on **Active Loads** and can only reach the docket flow. Health & Safety, Projects and the module grid
are locked — the same hard restriction the contractor dayworks login uses.

Bottom navigation for a haulier: **Dashboard** and **My Loads** only.

## 6. The docket

The existing Site Collection / Quarry Collection flow, unchanged, with one addition: a **read-only stamped
block** at the top of every docket showing

- Docket number
- Haulier (company)
- Driver name
- Vehicle reg

The driver never retypes these, and the office always knows who submitted what. Signatures (customer and
driver, draw-to-sign) and the docket photo work as they do today.

## 7. Two drivers, one lorry phone

**Switch driver on this lorry** on the Shift screen: company stays, name and reg clear, next driver types
theirs. Today's dockets stay attributed to whoever raised them.

---

## 8. What dropping the login costs — read before signing this off

These are the real trade-offs, not reasons to abandon the idea.

1. **Nobody is verified.** Anyone who can install the app and knows an approved haulier's name can submit
   dockets as that haulier. The approved-company list is the only thing standing in the way.
2. **The signature is weaker.** It's a drawn mark plus a self-typed name, not tied to an account. Fine for a
   delivery docket. It would **not** satisfy the account-tied signature requirement on the dayworks sheets.
3. **Drivers aren't deduplicated.** "J Kavanagh" and "John Kavanagh" are two different people to the system.
   The **reg** is the reliable key, not the name.
4. **Any approved haulier can submit against any customer** unless the customer list is restricted per
   haulier, or the office reviews dockets before they're billable.
5. **Driver names and mobiles are still personal data** even with no account, so they need a retention rule.

### The cheap safeguard, if 1 is too loose

A **4-digit job code** the site foreman reads out — one per site per week, typed once on the entry screen.
Keeps the no-login promise, but stops a stranger submitting dockets. Worth pricing as an option rather than
building it by default.

---

## 9. Open questions to confirm before build

1. Who maintains the approved haulier list — a new office admin screen, or the existing supplier list in the
   back office?
2. Does a haulier docket land straight in with employee dockets, or into a review queue the office approves
   first?
3. Should the customer list be restricted to the sites that haulier is actually working on?
4. Can a driver open and edit a docket after submitting, or is it locked?
5. Is the 4-digit job code in scope, or is the approved-company list enough?
6. Does the office need a live "which regs are on site now" view, or only completed dockets?
7. Is a customer signature mandatory on a haulier docket, or is the photo of the weighbridge docket enough?
8. How long are driver name and mobile kept after the job ends?
9. Does the haulier need to see their own docket history beyond today, or just today's loads?

---

## 10. Prototype

Interactive prototype covering all of the above: `public/index.html` in this repo. The notes panel beside the
phone maps each screen to the decisions in this document.
