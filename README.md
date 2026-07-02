# Global E-Commerce Sales Dashboard

An end-to-end data project built on the Tableau Sample Superstore dataset — covering exploratory analysis, ETL, and an interactive dashboard in Looker Studio.

## Dataset

**Source:** [Tableau Sample Superstore](https://community.tableau.com/s/question/0D54T00000CWeX8SAL/sample-superstore-sales-excelxls)  
**File:** `data/raw/superstore.csv`  
**Coverage:** 9,994 US retail orders across 4 regions, 2014–2017  
**Original encoding:** latin-1 (converted to UTF-8 during ETL)

## Project Structure

```
├── data/
│   ├── raw/               # Original unmodified source file
│   └── cleaned/           # ETL output, used by Looker Studio
├── notebooks/
│   ├── 01_EDA.ipynb       # Exploratory analysis
│   └── 02_ETL.ipynb       # Cleaning and feature engineering
├── scripts/               # Standalone Python scripts (future use)
├── data/DATA_DICTIONARY.md
└── README.md
```

## How to Run

```bash
source /home/mohamed/anaconda3/bin/activate practice_env
cd notebooks
jupyter lab
```
Run notebooks in order: `01_EDA.ipynb` → `02_ETL.ipynb`. The ETL notebook writes the cleaned file to `data/cleaned/superstore_clean.csv`.

## Dashboard

**Looker Studio:** [View Dashboard](https://datastudio.google.com/s/ssuzRNJDkxo)

## Key Findings from EDA

- 18.7% of orders are loss-making — concentrated in Furniture (Tables, Bookcases) and high-discount Office Supplies
- Discounts above 40% almost always result in negative profit
- Technology has the best profit margin (17.4%) despite not being the highest-revenue category
- Sales show clear year-end seasonality, peaking in November–December each year
