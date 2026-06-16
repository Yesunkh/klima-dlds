# WP1 — Data & setup: DONE

As of 15.06. Foundation for all other WPs. Source: DWD CDC (area-mean annual air temperature, 1881–2025).

## What is here
- `data/raw/regional_averages_tm_year.txt` — DWD raw file (= the data file we submit).
- `data/clean/temp_annual_regions.csv` — shared starting file, 145 rows × 18 columns, 0 NaN, checked.
- `klima_analyse.ipynb` — skeleton: sections 1–2 runnable (loads, cleans, saves the CSV), sections 3–8 as headings for the WPs.
- `WP_D1/ … WP_I2/` — one folder per analysis with task sheet (PDF + md) and a ready scratch template.
- `Collaboration.pdf` / `WP_Overview.md` — workflow contract and overview.

Verified: shape (145,18), years 1881–2025, 0 missing values, Germany mean 8.44 °C, warmest year 2024 = 10.89 °C, 2025 cooler (10.03 °C).

## Modularization contract (everyone)
1. Everyone starts from `data/clean/temp_annual_regions.csv` — not from the raw file.
2. Own scratch notebook per person. Do not co-edit `klima_analyse.ipynb`; one person merges at the end.
3. Entry (one cell): `df = pd.read_csv("data/clean/temp_annual_regions.csv")`.

## Task split (templates in `projekt_schritte.md`)
- D1 time series → Fig 1+2 (Block 2) · D2 by federal state → Fig 5 (Block 3) · I1 regression → Fig 3 (Block 4) · I2 bootstrap + t-test → Fig 4 (Block 5).
