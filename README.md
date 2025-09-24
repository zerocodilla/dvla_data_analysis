Portfolio data-analytics project

# Repo Description
This project analyses DVLA driving-licence snapshot tables (August 2025) in the UK to answer simple, practical questions:

- Which age and gender groups have the highest share of drivers with penalty points?
- Which postcode districts have the highest share of drivers with penalty points?
The work is intended as a compact, reproducible portfolio piece showing ETL, descriptive analytics, and clear storytelling.

# How to run

1. Put the Excel file driving-licence-data-aug-2025.xlsx in the repository root.
2. Open the notebook Untitled (1).ipynb in Jupyter / JupyterLab.
3. Install requirements (example):
```
pip install pandas matplotlib seaborn openpyxl
```
4. Run notebook cells in order. Outputs: CSVs and PNGs saved under results/ (created by the notebook).

# Data sources

Data source: https://www.data.gov.uk/dataset/d0be1ed2-9907-4ec4-b552-c048f6aec16a/driving-licence-data
Files: 
1. driving-licence-data-aug-2025.xlsx - DVLA snapshot.
Key sheets used:

- DRL0131 - August 2025 — Penalty points by age & gender
- DRL0101- August 2025 — Number of licences by age & gender
- DRL0102- August 2025 — Licences by postcode district
- DRL0132- August 2025 — Penalty points by postcode district

2. driving-licence-data-user-guide-sep-2017.docx — field descriptions and notes (used as reference).

# My assumptions

I make the following assumptions so results are reproducible and interpretable:

1. “Current” points vs historical totals: I treat penalty points 1..12 as the current operative range for routine analysis. Values greater than 12 appear in the raw table and reflect historical accumulation or exceptional cases; they are excluded from core % calculations.

2. Denominator (total drivers): Licence counts come from DRL0101 (provisional + full). I use these as denominators to compute percentages by age/gender.

3. District filtering: To avoid noisy percentages from very small populations, district-level results are shown only for districts with >= 100 full licences (this filter is applied in the notebook).

# Key findings
1. Age & gender: Middle-aged drivers show the highest counts and shares of penalty points. The female peak is roughly 41-50. Men show a similar middle-age concentration (with peak ranges slightly different).
<img width="1164" height="541" alt="Screenshot 2025-09-24 at 13 44 43" src="https://github.com/user-attachments/assets/999692c1-65db-485a-a51a-c56f41dfdb78" />

2. Overall gender difference: Male drivers have a higher share of drivers with penalty points than female drivers in this dataset (roughly ~2x).

3. Geography: After filtering districts with at least 100 full licences, the highest percent of drivers with penalty points appear in several West Yorkshire districts (e.g., LS23, LS14/LS15, HX areas) and pockets in Plymouth and Liverpool.
<img width="1150" height="527" alt="Screenshot 2025-09-24 at 13 44 55" src="https://github.com/user-attachments/assets/de62b55d-617d-4c32-8f02-3efd94b9cae6" />

This analysis can be useful for Insurance companies or Road Safety Teams for data-informed decisions.
