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

Add a third sign-in type — **Haulier** — that takes no credentials: the driver types their haulage company,
their name and their vehicle reg, and lands straight on Agg Loads to do dockets.

---

## 3. Who gets access

| Login type | Who | Credentials |
|---|---|---|
| Employee (existing) | Meaney staff | Password |
| Subcontractor (existing) | Subcontract crews | Password |
| **Haulier (new)** | Subcontracted haulage drivers | **None** |

Nothing is set up in advance — not the driver, and not the haulage company.

## 4. What the driver does

1. Taps **Haulier** on the Sign In screen.
2. Types **haulage company**, **driver name** and **vehicle reg**. Mobile optional.
3. Taps **Start doing dockets** — straight onto Active Loads.

All three are plain text fields. The device remembers them, so from the next day tapping **Haulier** goes
straight to Active Loads and the entry screen never appears again.

This is the lightest possible sign-in: a lorry that turns up for the first time this morning can be doing
dockets inside a minute, with no office involvement at all. Section 8 covers what that costs.

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

1. **There is no gate at all.** Anyone who can install the app can type any company and any name and submit
   dockets. Nothing is verified at sign-in, so every check has to happen in the office afterwards.
2. **Company names will drift.** You will get "Byrnes", "Byrne Haulage" and "byrne haulage ltd" as three
   names for one supplier. Someone has to map typed names onto real supplier accounts before self-billing
   can run — this is the main new office workload the change creates.
3. **The signature is weaker.** It's a drawn mark plus a self-typed name, not tied to an account. Fine for a
   delivery docket. It would **not** satisfy the account-tied signature requirement on the dayworks sheets.
4. **Drivers aren't deduplicated.** "J Kavanagh" and "John Kavanagh" are two different people to the system.
   The **reg** is the reliable key, not the name.
5. **Anyone can submit against any customer** unless the customer list is restricted per haulier, or the
   office reviews dockets before they're billable.
6. **Driver names and mobiles are still personal data** even with no account, so they need a retention rule.

### Where the check has to move to

Because nothing is stopped at the point of entry, the office needs a way to deal with it after the fact. Two
options worth pricing — neither is assumed in the prototype:

- **A review queue.** Haulier dockets land as unconfirmed until someone attaches them to a supplier account.
  Adds an office step, keeps the billing clean, and handles both problems 1 and 2 at once.
- **A 4-digit job code** the site foreman reads out — one per site per week, typed once on the entry screen.
  Still no accounts, but a stranger can't submit dockets. Addresses problem 1 only.

---

## 9. Open questions to confirm before build

1. How does a typed company name get matched to a supplier account for self-billing — office review, or fuzzy
   matching against the back office supplier list?
2. Does a haulier docket land straight in with employee dockets, or into a review queue the office approves
   first?
3. Should the customer list be restricted to the sites that haulier is actually working on?
4. Can a driver open and edit a docket after submitting, or is it locked?
5. Is the 4-digit job code in scope, or is an open sign-in acceptable?
6. Does the office need a live "which regs are on site now" view, or only completed dockets?
7. Is a customer signature mandatory on a haulier docket, or is the photo of the weighbridge docket enough?
8. How long are driver name and mobile kept after the job ends?
9. Does the haulier need to see their own docket history beyond today, or just today's loads?

---

## 10. Prototype

Interactive prototype covering all of the above: `public/index.html` in this repo. The notes panel beside the
phone maps each screen to the decisions in this document.
