# Health Center Quality Command Center

A single-file analytics dashboard for a multi-site Federally Qualified Health Center (FQHC), built as a work sample for the **Data Analyst / Health Data Analyst** role at **Alivio Medical Center** (Chicago). Each tab maps to a duty in the position description.

**Live demo:** `https://<your-username>.github.io/<repo-name>/`

> **All data is synthetic.** A seeded generator creates 14,000 patients and ~53,000 appointments shaped like a 4-site FQHC panel. No PHI, and nothing here describes Alivio's real performance.

## What it shows

| Tab | Question it answers |
|---|---|
| Executive overview | Where do we stand, and what needs attention this week? |
| UDS clinical quality | 13 UDS Table 6B/7 measures grouped into preventive, chronic disease, behavioral health, and maternal & child health, with HEDIS crosswalk, editable targets, site spread, and a Medicaid value-based-care view |
| Health equity | Disparity matrix of every measure by language, payer and age band, plus ranked largest gaps |
| Access & no-shows | No-show drivers: booking lead time, weekday × hour heatmap, site, portal vs phone, Saturday clinics |
| Finance & productivity | Visits per clinical FTE per day by provider, point-of-service (copay / sliding-fee) collection by site, visit forecast vs budget with editable seasonal assumptions |
| Care-gap worklist | Prioritized patient-level outreach list for CHW and front-desk huddles, exportable to CSV |
| Gap-closure planner | Will a measure hit target by Dec 31, given an outreach funnel with every assumption exposed? |
| Medicaid redetermination | Renewal pipeline by month and status, plus revenue at risk with editable PPS and lapse assumptions |
| Data quality & UDS | Extract validation checks, UDS cross-table reconciliation (3A = 3B = 4, Table 5 vs billed visits, denominator swings), reporting calendar |
| Methodology | Pipeline, KPI dictionary, measure definitions, sample CMS165 SQL, benchmark sources |

Filters for site, payer and language apply across every tab.

## Deploy on GitHub Pages (about 2 minutes)

1. Create a new public repository, for example `fqhc-quality-dashboard`.
2. Upload `index.html` and `README.md` to the root of the repository.
3. Go to **Settings → Pages**. Under **Source**, choose **Deploy from a branch**, then select `main` and `/ (root)`.
4. Wait about a minute. The site will be live at `https://<username>.github.io/fqhc-quality-dashboard/`.

There is no build step. Chart.js loads from cdnjs, and everything else is inline.

## Moving to real data

Swap the generator block in `index.html` (`/* RNG & GENERATION */`) for a JSON extract with the same fields: one row per patient (site, age, sex, payer, language, measure flags) and one row per appointment. In production that extract would come from a de-identified eClinicalWorks reporting view, refreshed nightly.

## Benchmark sources

- Hypertension control (63%) and uncontrolled diabetes (30%): HRSA, *2022 UDS Trends Data Brief*.
- Cervical (53%) and colorectal (42%) screening: national UDS figures cited in a NACHC health center field example (2019–2020 reporting).
- Replace these with the current-year UDS national and Illinois figures before using them in any real analysis.

---
Prepared by Abdul · demonstration only
