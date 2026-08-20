# Eastern Illinois Foodbank — Geospatial Analysis

Geospatial analysis of 25,000+ client visit records from the Eastern Illinois Foodbank, conducted as a volunteer data project through the **Statistics in the Community** club at the University of Illinois Urbana-Champaign.

---

## Overview

This project produces two geospatial views of Foodbank client data:

1. **Household origin map** — where clients are traveling from, aggregated by zip code across Illinois
2. **Agency distribution map** — which Foodbank locations clients are visiting, by zip code

Both maps are built as static choropleth maps (GeoPandas + Matplotlib) and interactive Folium maps. Findings were presented to Eastern Illinois Foodbank leadership to support resource allocation and service planning decisions.

---

## Key Findings

- Identified the highest-density client origin zip codes across Illinois, highlighting which communities rely most heavily on Foodbank services
- Mapped agency visit concentration to surface which locations serve the broadest geographic reach
- Dual-map approach allowed leadership to compare where clients come from vs. where they go — informing decisions about pantry placement and transportation access

---

## Tools & Methods

**Language:** Python  
**Libraries:** GeoPandas, Folium, Matplotlib, Cartopy, Shapely, Rasterio, Pandas, NumPy  
**Methods:** Zip-code level aggregation, choropleth mapping (static + interactive), geospatial joins with US Census boundary files

---

## Repository Structure

```
foodbank-geospatial-analysis/
├── README.md
├── FoodBank-py.ipynb          ← Main analysis notebook
├── requirements.txt
└── data/
    └── UIUC_Foodbank_censored.csv   ← Censored dataset (PII removed)
```

**Additional files required (not included due to size):**
- `cb_2018_us_zcta510_500k.shp` — US zip code boundary shapefile. Download from the [Census Bureau Cartographic Boundary Files](https://www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html)
- `IL_zip.json` — Generated automatically by the notebook on first run

---

## Data & Privacy Note

The original dataset contained personally identifiable information including date of birth, age, gender identity, race/ethnicity, disability status, employment status, and household composition. These fields have been removed from the published version (`UIUC_Foodbank_censored.csv`).

**Columns removed:** Household ID, date of birth, age, gender identity, race/ethnicity, disability status, employment, military status, household size, SNAP participation, and all individual-level demographic fields.  
**Columns retained:** Household zip code, household city/county/state, agency name, agency address, agency zip/city/county/state.

---

## How to Run

```bash
# Install dependencies
pip install -r requirements.txt

# Launch the notebook
jupyter notebook FoodBank-py.ipynb
```

Place `cb_2018_us_zcta510_500k.shp` (and its companion files) in the root directory before running. The notebook will generate `IL_zip.json` automatically.

---

## About

This project was completed as part of volunteer work with the [Statistics in the Community](https://stat.illinois.edu/) club at UIUC, which partners with local organizations to provide pro bono data analysis support.
