# Meaney App — Haulier Access

Interactive prototype for a **third sign-in type** in the Meaney app: **Haulier**, alongside the existing
Employee and Subcontractor logins.

Answering the client's question:

> "Is there a way that each driver doesn't have to have a profile and basically they add their company and
> name and away they go to be able to do dockets?"

Self-contained front-end prototype (single `public/index.html`, no backend, no data persistence beyond a
`localStorage` key used to demo the remembered device) served by a tiny zero-dependency Node server so it can
run on Railway.

## What it demonstrates

- **Sign In** screen matching the live app, with **Haulier** added under Employee / Subcontractor.
- **No-login entry**: haulage company, driver name and vehicle reg as plain text fields, plus optional mobile.
  Nothing is set up in advance — not the driver, and not the haulage company.
- **Day two is one tap**: a remembered lorry phone skips the entry screen and goes straight to Active Loads.
- **Switch driver on this lorry**: company stays, name and reg clear — for two drivers sharing one phone.
- **Agg Loads dashboard** matching the live app (Show Filters, Active Loads table, New Load / Back), with
  Health & Safety, Projects and the module grid visibly locked.
- **Docket flow**: Site / Quarry collection picker, docket form with the haulier, driver and reg
  **stamped read-only at the top**, cascading category → type, weight.
- **Draw-to-sign** customer and driver signatures on canvas (clear & re-sign), plus docket image capture.
- **My Shift**: dockets and tonnes today, who's signed in, switch driver, end shift & forget device.
- **Notes panel** beside the phone explaining each decision, what an open sign-in costs (no gate at all,
  company names drifting, weaker signature), where the check has to move to instead, and the open questions
  to confirm before build.

## Run locally

```bash
npm start
```

Then open http://localhost:3000

No Node on the machine? Any static server over `public/` works:

```bash
python3 -m http.server 8751 --directory public
```

## Deploy on Railway

1. Push this repo to GitHub.
2. In Railway: **New Project → Deploy from GitHub repo** → select this repo.
3. Railway auto-detects Node (Nixpacks), runs `npm install` then `npm start`.
4. The server binds to `process.env.PORT` automatically. Health check: `/healthz`.

No environment variables are required.

## Related

- `../meaneycontractorsdashboard` — the contractor dayworks hub prototype (separate proposed change).
- `Proposed_App_Changes_Haulier_Access.md` — the written spec that goes with this prototype.
