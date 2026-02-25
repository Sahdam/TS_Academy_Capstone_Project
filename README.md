# TS_Academy_Capstone_Project
## 🇳🇬 Food Basket Price & Food Inflation Forecasting
### TS Academy — Track 3: Time Series Analysis | Capstone Project

---

## 📌 Project Overview

Nigeria has experienced severe food price inflation over the past decade, with conditions worsening significantly following the removal of the fuel subsidy in May 2023. This capstone project builds a **time series forecasting system** for two critical economic indicators:

- **Basket Price** — a weighted composite of 14 staple food commodities reflecting the real cost of a typical Nigerian household's monthly food spend
- **CPI Food** — the official Consumer Price Index for food, as published by the National Bureau of Statistics (NBS)

By modelling both indicators simultaneously and linking them through a **cascade forecasting architecture**, we produce 6-month ahead forecasts that can inform household planning, policy decisions, and economic analysis.

---

## Problem Statement

Food affordability is one of the most pressing economic challenges facing Nigerian households today. Between 2022 and 2024, food prices surged by over 80% in nominal terms, driven by:

- The removal of the petrol subsidy in June 2023, which caused immediate and severe cost-of-living shocks
- Persistent naira depreciation against the US dollar, raising the cost of imported food and inputs
- Supply chain disruptions and structural inefficiencies in local food markets

Despite the severity of the crisis, reliable short-term forecasts for food prices remain scarce. Existing tools either rely on lagged official data or fail to account for structural breaks caused by policy changes.

This project addresses that gap by developing **data-driven time series models** that:

1. Explicitly model the 2023 structural break using shock dummy variables
2. Incorporate macroeconomic drivers (fuel price, exchange rate) as exogenous regressors
3. Validate a linked architecture where basket price forecasts improve CPI food predictions
4. Quantify forecast uncertainty through GARCH volatility modelling

---

## Project Objectives

- Achieve a **Mean Absolute Percentage Error (MAPE) below 5%** on both target variables
- Identify and account for the **structural break** caused by the 2023 fuel subsidy removal
- Build a **reproducible, modular forecasting pipeline** split across team notebooks
- Generate **6-month forward forecasts** (November 2025 – April 2026) for both targets
- Demonstrate the value of **linked modelling** — using basket price to improve CPI food predictions

---

## Dataset

| Detail | Description |
|--------|-------------|
| **Source** | `Inflation_data.csv`, `PMS_Price.csv`, `Exchange_rate.csv`, `Selected_food_price.csv` (all available in this repository) |
| **Coverage** | January 2017 – January 2026 (monthly frequency) |
| **Key variables** | Basket commodity prices (eggs, beans, bread, chicken, garri, maize, onions, palm oil, rice, tomatoes, vegetable oil, yam, sweet potato), CPI Food, CPI All Items, fuel price (PMS), exchange rate (NGN/USD) |
| **Frequency** | Monthly (`ME` — month-end) |
| **Missing values** | Handled via time-series interpolation |

### Basket Price Formula
The basket price is a **weighted sum** of 14 commodities, reflecting typical Nigerian household consumption quantities:
```python
basket_price = eggs + 3×beans + 4×bread + 2×chicken + 4×garri + 2×maize
             + onions + 2×palm_oil + 3×rice_local + 3×rice_imported
             + 3×tomatoes + 2×vegetable_oil + 2×yam + 3×sweet_potato
```

---

## 👥 Team & Role Assignments

> **Team Lead** participates in and oversees all sections of the project.

| Role | Section | Notebook | Team Members |
|------|---------|----------|--------------|
| **Team Lead** | All sections | All notebooks | Team Lead *Olayinka Yusuf* |
| **Team A** | Exploratory Data Analysis |`00_data_preprocessing_eda.ipynb` | Agunbiade Simbiat Mogbonjubola, Abeeb Olasupo, Chinecherem Victoria Isaac |
| **Team B** | Stationarity & ACF/PACF | `01_stationarity_acf_pacf.ipynb` | JOHN MERCY OMETERE, Ademola Adeyemi , Odukaiye Moses |
| **Team C** | basket_price Modelling | `02_basket_price_models.ipynb` | Ojumoola Paul, Orinya Samuel Obande, Abdulmalik Abdulrashid |
| **Team D** | cpi_food Modelling & Forecasts | `03_cpi_food_and_forecasts.ipynb` | Maria Ebimo Ebiakofa, Fayemi Anthony Olatokunbo, @Sopuruchilizbeth |

### What Each Team Does

**Team Lead — Setup & Data Preprocessing**
- Creates and manages the GitHub repository
- Reviews and integrates all team submissions
- Work with every team in their respective notebooks

**Team A — Exploratory Data Analysis** (`00_data_preprocessing_eda.ipynb`)
- Runs data loading, cleaning, type conversion, and interpolation
- Engineers the basket price composite and derived features
- Produces the clean `df` dataframe used by all teams
- Time series plots for basket_price and cpi_food (level, MoM%, YoY%)
- Correlation heatmap of all variables
- Written markdown interpretations of all findings

**Team B — Stationarity & Diagnostics** (`01_stationarity_acf_pacf.ipynb`)
- Seasonal decomposition (trend, seasonal, residual components)
- ADF and KPSS tests on both series at the level and first difference
- ACF and PACF plots on differenced series
- Written stationarity conclusions and ARIMA order recommendations

**Team C — basket_cost Modelling & Forecasts** (`02_basket_price_models.ipynb`)
- Train/test split (train: Jan 2017 – Jul 2025 | test: Aug – Oct 2025)
- ARIMA baseline model
- SARIMAX with and without exogenous variables
- GARCH(1,1) volatility analysis on residuals
- 6-month forward forecasts for basket_cost (Nov 2025 – Apr 2026)
- Model comparison table and actual vs predicted visualisation

**Team D — cpi_food Modelling & Forecasts** (`03_cpi_food_and_forecasts.ipynb`)
- Shock dummy creation (shock_onset: Mar–Dec 2023, shock_persist: 2024)
- cpi_food standalone SARIMAX model
- cpi_food linked model (using basket_price forecasts as regressor)
- 6-month forward forecasts for food inflation (Nov 2025 – Apr 2026)
- Model comparison table and actual vs predicted visualisation
- Final dual-panel visualisations

---

## Repository Structure
```
TS_Academy_Capstone_Project/
│
├── Project_Data - Sheet1.csv          # Raw dataset
├── README.md                          # This file
│
├── 00_data_preprocessing_eda_decomposition.ipynb         # Team A: EDA
├── 01_stationarity_acf_pacf.ipynb    # Team B: stationarity
├── 02_basket_price_models.ipynb      # Team C: basket_price models
└── 03_cpi_food_and_forecasts.ipynb   # Team D: cpi_food + forecasts
```

---

## How to Run

1. Open [Google Colab](https://colab.research.google.com)
2. Go to **File > Open notebook > GitHub tab**
3. Search for `TS_Academy_Capstone_Project`
4. Open your assigned notebook
5. Run the dataset loading cell at the top **before any other cell**
6. Work through your assigned cells
7. Save back to GitHub via **File > Save a copy in GitHub**

> **Never work from a Google Drive copy. Always open directly from GitHub.**

---

## Dependencies
```python
pandas
numpy
matplotlib
statsmodels
pmdarima
scikit-learn
arch
```

All packages are pre-installed in Google Colab. No additional setup required.

---

*TS Academy — Track 3: Time Series Analysis | Capstone Project*
