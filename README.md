# IndustrialOps v0.1

A static, GitHub Pages-compatible prototype for manufacturing shift reporting and SQDCM operations. Built with plain HTML, CSS and JavaScript — no build step or paid service required.

## Features

- Manufacturing overview with KPI cards and a 7-day output trend
- Create, edit, search and filter shift reports
- Production line settings, shift definitions and target quantities
- Incident register with severity, ownership, due dates and status
- CSV report export and CSV import with basic validation
- JSON backup export
- Browser-local audit history
- Responsive desktop/tablet/mobile layout
- Synthetic starter data

## Run locally

Open `index.html` in a modern browser. Some browser configurations restrict local-file storage; if so, serve the folder with a local static server, e.g. `python -m http.server 8000`, then open `http://localhost:8000`.

## Publish with GitHub Pages

1. Create a new GitHub repository, for example `industrialops`.
2. Upload `index.html` and `README.md` to the repository root.
3. Open **Settings → Pages**.
4. Under the build/deployment section, choose **Deploy from a branch**.
5. Choose branch `main` and folder `/ (root)`, then save.
6. Wait for the Pages deployment to finish. Your site URL will be shown in the Pages settings.

## CSV import columns

The importer expects these headers (case-insensitive): `date,shift,lineId,target,good,scrap,downtime`. Optional headers: `id,lineName,planned,status,operator,comments`. `lineId` should match a configured line ID (e.g. `L1`) or you can supply `lineName` matching a configured line. Duplicate line/date/shift records are skipped.

## Important prototype limitations

- All data is stored in `localStorage` in the current browser profile. Visitors to the GitHub Pages URL do **not** share data with each other.
- This is not authentication, access control, a secure multi-tenant SaaS, or a validated quality management system.
- The audit history is client-side and can be modified by someone with browser developer tools.
- Do not enter confidential, personal, regulated or real production data.
- KPI definitions must be agreed with the factory before operational use.

## Roadmap

1. Gather a real (authorized and sanitized) spreadsheet workflow and confirm formulas.
2. Add automated tests and stronger input validation.
3. Move data to PostgreSQL and enforce tenant isolation and roles on the server/database.
4. Add server-side audit events, authentication, backups, migrations and monitoring.
5. Add configurable forms and additional modules only after the first workflow is validated.
