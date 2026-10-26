# LITUS

**Predictive Mapping of Sargassum Proliferation through Satellite Imagery and Oceanographic Data**

LITUS is a proposed web-based decision-support tool that helps Boracay stakeholders monitor Sargassum sightings and prepare for possible shoreline accumulation. This repository contains the hackathon demo: a public site where community members can submit field reports, and a staff dashboard where authorised responders review them.

> **Demo only.** All observations are illustrative sample data, not live detections. Reports are not sent to local authorities and do not verify actual Sargassum presence. Always confirm conditions in the field before making operational decisions.

Built by Team **Bitcrushers** for CS Bootcamp 2026.

## Pages

| Page | File | Audience | Purpose |
|------|------|----------|---------|
| Public site | `index.html` | Everyone | Project proposal, prototype workspace, and the field report form |
| Staff dashboard | `dashboard.html` | Authorised staff | Map, inspection priorities, report table, CSV export |

## How the two pages connect

1. A visitor submits a field report (location, status, accumulation level, date, time, notes) on the public site.
2. The report is saved to browser `localStorage` under the key `litus-demo-reports-v1`.
3. The staff dashboard reads the same key, so the new report appears in the metrics, map, priority list and table. If both pages are open, it updates automatically and shows a toast.

## Staff access

The dashboard opens on a sign-in screen. Demo access code: `LITUS-2026`.

This gate runs entirely in the browser and the code is visible in the page source. It is a demo of the access-controlled flow, **not real security**. Do not use it to protect real data.

## Features

**Public site**
- Project proposal: problem, objectives, operations, budget, limitations, references
- Prototype workspace with sample observations, status filters and a schematic Boracay map
- Working field report form

**Staff dashboard**
- Coastal overview with summary metrics
- Interactive schematic map with status markers
- Inspection priorities (high accumulation first)
- Searchable and filterable report table, with a detail panel
- Field reports, satellite, and cleanup-priority views
- Add reports manually, export all reports to CSV
- Light and dark themes

## Run locally

It is a static site with no build step. Open `index.html` in a browser, or serve the folder so both pages share storage reliably:

```bash
python -m http.server 8000
# then open http://localhost:8000
```

Opening files directly (`file://`) works in Chrome, but Firefox and Safari may not share `localStorage` between the two pages. Use a local server if reports don't appear in the dashboard.

## Deploy to Vercel

1. Push this repository to GitHub.
2. In Vercel, choose **Add New → Project** and import the repo.
3. Framework preset: **Other**. No build command. Output directory: the project root.

`vercel.json` enables clean URLs, so the dashboard is served at `/dashboard`.

## Project structure

```
.
├── index.html       # public site + report form
├── dashboard.html   # staff dashboard
├── vercel.json      # clean URLs and basic headers
└── README.md
```

## Limitations

- **Per-browser storage.** Reports live in each visitor's own browser, so a report submitted on one device will not appear on another device's dashboard.
- **No real authentication** (see Staff access).
- **Sample data.** Seeded observations are illustrative. No live satellite or oceanographic feeds are connected.
- **No forecasting model.** The prototype prioritises a working, testable dashboard over reliable beaching forecasts.

## Roadmap

- Shared backend (e.g. Supabase or Firebase) so reports sync across devices
- Real authentication and role-based access for staff
- Live Sentinel-2 satellite observations and wind/ocean-current data
- Photo uploads on field reports
- Threshold-based alerts

## Data sources referenced

- [Copernicus Sentinel-2](https://dataspace.copernicus.eu/data-collections/copernicus-sentinel-missions/copernicus-sentinel-2)
- [CopPhil (Philippines access to Copernicus data)](https://infra.copphil.philsa.gov.ph/)
- [Sargassum Information Hub](https://sargassumhub.org/monitoring/research/)

## Team

Bitcrushers, CS Bootcamp 2026.
