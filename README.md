# Round Hill water system: asset age and replacement forecast

Live replacement-cost dashboard for the Town of Round Hill water system. Replaces the earlier static version.

## How it updates
- **Assets** are read live from the town's GIS (`Water_Management_Layer_2_view`, layers 0-4) every time the page loads. New assets are picked up automatically; assets marked abandoned, removed or proposed are left out.
- **Install years, sizes, materials and lengths** come from the GIS where they are filled in, otherwise from `data/assets_baseline.csv` (the install history rebuilt from plan records in 2026).
- **Unit prices and useful lives** come from `data/unit_prices.csv`, a copy of the town's price and life table (RoundHill_prices_and_life.xlsx). Meters use the GIS replace value when it is filled in. Edit a price there (in GitHub: open the file, click the pencil, change the number, commit) and the dashboard recalculates on its next load.
- If a GIS layer can't be read, that asset type falls back to the baseline list and the page says so.

## Files
| File | Purpose |
|---|---|
| `index.html` | The dashboard |
| `data/unit_prices.csv` | Unit prices and useful lives from the town's price and life table |
| `data/assets_baseline.csv` | Baseline install year, size, material and length for each asset, keyed by GIS GlobalID |

## Settings
The `CONFIG` block near the bottom of `index.html` holds the GIS layer URLs, the file paths, and the link to the hydrant and valve maintenance dashboard. The view layers must stay shared publicly for the page to read them.

Planning-level construction cost estimates prepared by Bowman Consulting. Not engineering estimates for a specific project.
