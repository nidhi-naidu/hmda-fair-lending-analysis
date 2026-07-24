# HMDA Fair Lending Analysis — Washington DC MSA (2023)

**Do location and race affect mortgage loan approval, even when applicants have similar financial profiles?**

This project analyzes 59,479 home purchase loan applications from the 2023 HMDA (Home Mortgage Disclosure Act) dataset for the Washington DC Metropolitan Statistical Area, combining spatial analysis, statistical testing, and machine learning to investigate racial and geographic disparities in mortgage approval outcomes.

> Academic and research project. Not legal or regulatory advice.

## 🔗 Live Demos

- **Interactive Dashboard:** [hmda-fair-lending-dashboard.streamlit.app](https://hmda-fair-lending-dashboard.streamlit.app/) — includes the interactive denial-rate map
- **Write-up:** [Medium article — "We Analyzed 59,000 Mortgage Applications in Washington D.C."](https://medium.com/@nidhi.naidu/we-analyzed-59-000-mortgage-applications-in-washington-d-c-f3cee358b98b)

## Key Findings

| Metric | Result |
|---|---|
| Raw Black–White approval gap | 9.1 percentage points |
| Gap after controlling for DTI/LTI/LTV | 10.3 percentage points |
| Spatial clustering (Moran's I) | 0.267 (p = 0.001) |
| Logistic regression odds ratio (race) | 0.665 |
| Model performance | XGBoost + SHAP explainability |

## Dataset

- **Source:** [FFIEC Public HMDA Data Platform](https://ffiec.cfpb.gov/data-publication/2023), 2023 vintage
- **Scope:** Washington DC MSA (code 47894), home purchase loans only
- **Size:** 168,137 raw applications filtered to 59,479 with final decisions, matched across 1,095 census tracts (97.7% match rate to Census TIGER 2023 shapefiles)

## Methodology

The analysis was structured in five phases:

1. **Data Acquisition, Spatial Setup & EDA** — cleaned and filtered raw HMDA records, matched applications to census tract shapefiles, computed raw approval gaps, and built the interactive Folium choropleth denial-rate map.
2. **Feature Engineering & Demographic Analysis** — engineered DTI, LTI, and LTV features with imputation to isolate the corrected approval gap.
3. **Spatial & Statistical Analysis** — tested for spatial autocorrelation (Moran's I) and ranked lenders by approval disparity.
4. **Modeling & Explainability** — logistic regression and XGBoost models with SHAP values to interpret the role of race alongside financial variables.
5. **Dashboard Export** — packaged model outputs and statistics into a Streamlit app with an AI-assisted analyst view.

## Tech Stack

Python · Pandas · GeoPandas · scikit-learn · XGBoost · SHAP · Folium · PySAL/ESDA (spatial statistics) · Streamlit

## Repository Structure

```
├── notebooks/
│   └── hmda_fair_lending_analysis.ipynb   # Full analysis, all 5 phases
├── dashboard/
│   ├── tract_stats.csv
│   ├── lender_disparity.csv
│   ├── key_stats.json
│   └── tracts.geojson
└── README.md
```

*Raw HMDA data is not included in this repo due to size — it can be downloaded directly from the [FFIEC source](https://ffiec.cfpb.gov/data-publication/2023).*

## Team

Built by [Nidhi Naidu](https://github.com/nidhi-naidu) and [Hritik Majgaonkar](https://github.com/HritikMajgaonkar) as a capstone project.
