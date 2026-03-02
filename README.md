# TS_Academy_Capstone_Project
## 🇳🇬 Food Basket Price & Food Inflation Forecasting
### TS Academy — Track 3: Time Series Analysis | Capstone Project

---

## Project Overview

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


### Contributors
|Name|Email| Github Link|
|---|---|---|
|1. Ojumoola Paul|ojumoolatimi@gmail.com|https://github.com/ojumoolatimi |
|2. JOHN MERCY OMETERE| princessade463@gmail.com|https://github.com/MercyJ01 |
|3. Abdulmalik Abdulrashid|abdulmalikabdulrashid1@gmail.com|https://github.com/Abd00lmalik |
|4. Chinecherem Victoria Isaac|chinecheremisaac25@gmail.com| |
|5. Fayemi Anthony Olatokunbo|tonitokunbo@gmail.com|https://github.com/tonitokunbo |
|6. Agunbiade Simbiat Mogbonjubola| mogbonjubola1999@gmail.com|https://github.com/simbiatagunbiade |
|7. Abeeb Olasupo| olasupohabeeb219@gmail.com|https://github.com/habeeb-szn |
|8. Ademola Adeyemi| Ademolaadeyemi719@gmail.com|https://github.com/Demola111 |
|9. Odukaiye Moses| mosesx3m0@gmail.com|https://github.com/mosesx3m |
|10. Orinya Samuel Obande| samuelorinys7@gmail.com|https://github.com/Phanerusis |
|11. Olayinka Yusuf| yusufolayinka92@gmail.com|https://github.com/Sahdam |
|12. Maria Ebimo Ebiakofa| Mariaebimo@gmail.com|https://github.com/Mia-Ebimo |
|13. Sopuruchi | | sopuruchilizbeth@gmail.com|

---

## Team & Role Assignments

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
## EDA — Plot Analyses

---

### Basket Cost Time Series

**Observation**  
Basket cost remained largely flat between ₦17,000–₦20,000 from 2017 to 2019, with gradual growth to ₦35,000 by mid-2023. After the June 2023 subsidy removal, prices surged aggressively, peaking above ₦100,000 in early 2025 before a modest decline to ~₦94,000 by 2026.

**Key Findings**
- The 2019 border closure and 2020 COVID lockdown produced no visible level shift — prices absorbed both events without structural disruption
- The June 2023 subsidy removal + FX unification is the dominant event — basket cost nearly **tripled** within 18 months
- The 2024 further FX depreciation accelerated the surge to its peak
- Post-2025 decline suggests some price stabilisation but at a permanently higher plateau

**Modelling Implication**  
The sharp non-linear jump confirms the need for shock dummy variables. A model trained on pre-2023 data alone would severely underestimate current price levels.

---

### Food CPI Time Series

**Observation**  
CPI Food grew steadily from ~230 in 2017 to ~650 by mid-2023, then accelerated sharply to a peak of ~1,240 by late 2025, before declining slightly to ~1,160 in early 2026.

**Key Findings**
- Growth was continuous and persistent even before the shock — food inflation was already structurally elevated
- The border closure (2019) and COVID lockdown (2020) caused brief pauses but no reversals
- The subsidy removal triggered the steepest acceleration — CPI Food nearly **doubled** within 18 months of the shock
- The slight decline in 2026 mirrors the basket cost pattern — both indicators are cooling from their peaks but remain historically high

**Key Difference from Basket Cost**  
CPI Food began accelerating earlier (from 2022 onward), suggesting it captured global commodity price pressures from the Russia-Ukraine war before they fully transmitted into raw basket commodity prices.

---

### Basket Cost MoM & YoY Time Series

**Observation**  
MoM% (red) remained low and stable throughout the sample, fluctuating between −5% and +15%. YoY% (blue) tells a dramatically different story — climbing from ~20% in 2020 to a peak of **127% in early 2024**, then declining sharply toward 0% and briefly negative by 2026.

**Key Findings**
- MoM% spikes are short-lived and mean-reverting — individual months of sharp increase are always followed by moderation
- The YoY% peak of 127% in early 2024 reflects the full annualised impact of the June 2023 shock
- The rapid YoY% decline from 2024 onward is a **base effect** — as the shock period enters the comparison window, the year-on-year gap narrows even if prices remain high
- Negative YoY% approaching 2026 signals that basket prices are now **lower than a year earlier** — a genuine cooling from the peak

**Modelling Implication**  
The volatility spike in MoM% post-2023 justifies GARCH modelling — variance is clearly not constant across the sample.

---

### Food CPI MoM & YoY Time Series

**Observation**  
MoM% (red) remained extremely stable between 0–3% throughout the full period with only minor post-2023 spikes. YoY% (blue) climbed from ~13% in 2018 to a peak of ~40% in early 2024, then declined sharply to ~9% by early 2026.

**Key Findings**
- CPI Food MoM is far more stable than basket cost MoM — the official index is smoother by construction
- The YoY% peak of ~40% (early 2024) is lower than basket cost's 127% peak, confirming CPI measures a broader, more buffered indicator
- The sharp YoY% decline from 2024 to 2026 is primarily a base effect, not a genuine deflation
- The brief negative MoM% dip in 2025 is notable — it reflects months where CPI Food actually fell month-on-month, likely driven by seasonal harvest improvements

---

### Basket Cost MoM Distribution

**Observation**  
The distribution is roughly bell-shaped and centred near 0%, with most months recording MoM changes between −3% and +5%. There are right-skewed outliers extending to +13–15%, and a small number of negative outliers around −7%.

**Key Findings**
- The near-zero centre confirms basket cost is relatively stable month-to-month in normal conditions
- The right tail (extreme positive months) corresponds to shock-period months in 2023–2024
- The distribution is **positively skewed** — large positive surprises are more common than large negative ones
- The outliers at +13–15% are the shock-onset months and should be treated as structural rather than random

**Modelling Implication**  
The fat right tail and positive skew justify using Student-t distributed errors in GARCH — a normal distribution would underestimate tail risk.

---

### Food CPI MoM Distribution

**Observation**  
Unlike basket cost, this distribution is **heavily right-skewed with no left tail**. Almost all observations are positive (0% to 4%), with two isolated extreme outliers near −6% and −2%.

**Key Findings**
- CPI Food almost never declines month-on-month — the two negative outliers are rare anomalies
- The concentration between 1–3% MoM reflects the persistent, structural nature of food inflation in Nigeria
- There is no symmetric distribution here — this is a **one-directional inflation process**
- The outliers at −6% are likely data revisions or seasonal deflation episodes (e.g. post-harvest gluts)

**Modelling Implication**  
The absence of a left tail means standard symmetric error distributions (Gaussian) are inappropriate. This supports the use of non-normal residual distributions in model fitting.

---

### Pre vs Post Shock (Basket Cost & CPI Food)

**Observation**  
Both panels clearly show two distinct regimes separated by the June 2023 dashed line. The pre-shock green zone shows gradual growth; the post-shock red zone shows near-vertical acceleration.

**Key Findings**
- **Basket Cost**: pre-shock range was ₦17,000–₦35,000 over 6 years; post-shock range is ₦35,000–₦103,000 — a **194% increase in under 2 years**
- **CPI Food**: pre-shock range was 230–650; post-shock range is 650–1,240 — a **91% increase** in the same period
- The slope change at the shock date is visually unambiguous in both panels
- Both series show slight moderation post-2025 peak but remain firmly in the post-shock regime

**Modelling Implication**  
The visual regime change confirms the structural break. Any model without shock dummies will have systematically biased residuals across the post-2023 period.

---

### Correlation Heatmap

**Observation**  
The entire heatmap is uniformly dark green — all correlations are between **0.89 and 1.00**. There are no negative or even moderate correlations anywhere in the matrix.

**Key Findings**
- **Basket Cost** correlates at 0.97–1.00 with bread, local rice, foreign rice, and vegetable oil — these are its primary price drivers
- **Food CPI** correlates at 0.94–0.99 with all commodities and macro drivers — it moves closely with the entire system
- **Exchange Rate** (0.99) and **Fuel Price** (0.97) are both near-perfectly correlated with basket cost — confirming their role as macro drivers
- **Tomatoes** (0.91–0.95) and **Brown Beans** (0.89–0.97) show slightly lower correlations — reflecting more volatile, weather-dependent supply
- **Chicken** shows the lowest correlation with Food CPI (0.98) — still very high but slightly more independent, possibly due to poultry-specific supply dynamics

**Key Caution**  
The uniformly high correlations are partly driven by the shared upward trend (non-stationarity). These correlations reflect co-movement over time, not necessarily causal relationships. Always interpret alongside differenced or detrended analysis.

---

### Scatter Plot: Basket Cost vs Exchange Rate & Fuel Price

**Observation**  
Both scatter plots show near-perfect linear relationships — overall fit r=0.99 (exchange rate) and r=0.97 (fuel price). Pre-shock blue dots cluster tightly at low values; post-shock red dots extend to the upper right.

**Key Findings**
- **Exchange Rate**: pre-shock r=0.92, post-shock r=0.93 — strong and consistent across both periods, with the post-shock period extending the range to ₦800–₦1,700/USD
- **Fuel Price**: pre-shock r=0.87, post-shock r=0.86 — similarly strong, with fuel price jumping from ~₦180/litre to over ₦1,200/litre post-shock
- The pre- and post-shock regression lines follow nearly identical slopes — the **transmission rate** did not change, only the *level* of the drivers did
- A few post-shock red dots fall below the regression line — months where exchange rate spiked but basket prices had not yet fully adjusted

**Modelling Implication**  
The strong, stable linear relationships across both periods validate exchange rate and fuel price as exogenous regressors in SARIMAX. The relationship is structural, not regime-specific.

---

### Rolling 12-Month Correlation

**Observation**  
Both panels show a clear strengthening of correlation after June 2023, though with different patterns.

| Driver | Pre-Shock Avg | Post-Shock Avg | Pattern |
|---|---|---|---|
| Exchange Rate | r = 0.41 | r = 0.69 | Volatile pre-shock, strong then collapsed in 2025 |
| Fuel Price | r = 0.27 | r = 0.72 | Episodic pre-shock, sustained post-shock |

**Key Findings**
- **Exchange Rate**: the correlation was already climbing toward 1.0 pre-2023 (from 2020 onward), suggesting FX pressure was building before the official shock. The collapse toward 0 in late 2025 indicates a period where exchange rate stabilised while basket prices continued moving independently
- **Fuel Price**: transformed from a cyclical, episodic relationship to a sustained high correlation post-shock — confirming fuel became a **continuous structural driver** after subsidy removal
- **Fuel price (r=0.72) is the more reliable post-shock driver** — it remained consistently above 0.7 without the volatility seen in the exchange rate correlation

**Modelling Implication**  
Both macro drivers are justified as exogenous regressors. The post-shock sustained correlations confirm they belong in the model, and the pre-shock instability explains why shock dummies are necessary to handle the regime change.

---

### Individual Commodity Price Trends

**Observation**  
All 14 commodities clustered tightly below ₦500/unit from 2017–2022, then diverged sharply post-2023. By 2025, prices had separated into distinct tiers.

**Key Findings**
- **Eggs** and **Local Rice** are the highest-priced commodities — eggs spiked to ~₦7,500 and local rice peaked at ~₦6,500 in 2025 before partial correction
- **Chicken** reached ~₦6,500 at peak — reflecting sensitivity to both feed costs (maize-driven) and cold chain fuel costs
- The majority of commodities (maize, garri, yam, tomatoes, onions, vegetable oil, palm oil) converged to a ₦1,000–₦2,500 range post-shock — a **4–8× increase** from pre-shock levels
- **Bread** shows a relatively flatter post-shock trajectory — reflecting some price stickiness at retail level
- The spike-and-partial-correction pattern in eggs and local rice suggests **speculative price overshooting** followed by market correction

---

### Stacked Area Chart: Commodity Contributions

**Observation**  
The total weighted basket was stable at ~₦17,000–₦20,000 from 2017 to 2020, grew gradually to ~₦35,000 by 2023, then surged to a peak of ~₦103,000 in 2025. The composition of contributions also widened dramatically.

**Key Findings**
- **Pre-shock**: all commodity layers were thin and evenly distributed — no single commodity dominated
- **Post-shock**: the stack more than doubled in height, with **garri, local rice, vegetable oil, and chicken** showing the most visible expansion
- **Garri and local rice** — despite being locally produced staples — show large post-shock contribution expansions, driven by transport cost inflation and domestic supply disruptions
- The visible thickening of almost every layer confirms the shock was **broad-based** — all 14 commodities contributed to the surge

---

### % Change in Weighted Contribution (Pre vs Post Shock)

**Observation**  
Every single commodity recorded a positive post-shock contribution increase, ranging from **+158.3% (chicken)** to **+473.3% (yam)**. All bars are red — no commodity was immune to the shock.

| Rank | Commodity | % Change | Reason |
|---|---|---|---|
| 1st | Yam | +473.3% | Highly transport-dependent, no cold storage, severe logistics cost pass-through |
| 2nd | Potatoes | +349.3% | Similar logistics exposure, perishable |
| 3rd | Local Rice | +340.6% | Domestic supply chain + fuel costs for milling and transport |
| 4th | Brown Beans | +332.9% | Major Northern supply regions hit by insecurity + transport costs |
| 5th | Maize | +316.0% | Feed grain for poultry and livestock — ripple effect across animal products |
| Last | Chicken | +158.3% | Partially buffered by vertical integration in the poultry industry |

**Key Findings**
- The **top 5 are all locally produced staples** — contradicting the assumption that import-dependent items suffer most. Local food supply chains proved equally vulnerable to fuel cost transmission
- **Chicken's relatively low increase** (+158%) reflects that large-scale poultry producers partially absorbed cost increases through operational efficiencies
- The uniformity of increases across all 14 items confirms a **systemic shock** rather than commodity-specific disruptions

**Modelling Implication**  
The broad-based nature of the shock validates using a single structural break dummy for the entire basket rather than commodity-specific interventions.

---

### Basket Cost and Food Inflation CUMSUM

The CUSUM analysis provides formal statistical confirmation of the structural 
break identified visually in the level plots. Key findings:

1. **Basket Cost structural break**: June 2023 — coincides exactly with the fuel 
   subsidy removal and CBN exchange rate unification, confirming these policy 
   events as the primary driver of the price regime change.

2. **CPI Food structural break**: August 2022 — approximately 10 months earlier,
   reflecting global commodity shocks (Russia-Ukraine war) and pre-existing 
   naira weakness that transmitted into broader food inflation before the 
   official policy shock.

3. Both series breach the ±2σ statistical bounds, confirming the breaks are 
   genuine regime changes and not random variation.

4. The V-shaped recovery in both series confirms that post-shock price growth 
   was so rapid it fully offset years of below-average readings, establishing 
   a permanently higher price plateau.

These findings justify the use of shock dummy variables (shock_onset and 
shock_persist) in all SARIMAX specifications, and confirm that any model 
trained on pre-2022 data alone would severely underestimate current and 
future food price levels.

---
*TS Academy: Time Series Analysis | Capstone Project*
