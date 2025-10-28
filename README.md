# DSA210
for DSA 210 project


# 💱 Zara Sales Analysis: The Impact of Exchange Rate and Inflation on Sales Volume

## 🎯 Motivation

In today’s globalized retail environment, **macroeconomic indicators** such as currency fluctuations and inflation have a profound effect on consumer purchasing behavior.  
For international fashion brands like **Zara**, which imports materials and adjusts prices dynamically, these economic variables can directly influence sales volume, profit margins, and inventory strategy.

The goal of this project is to analyze whether **exchange rate and inflation levels** significantly impact Zara’s **sales volume** over time.  
By linking store-level sales with macroeconomic data, the project aims to uncover patterns in how economic volatility affects retail performance and consumer behavior.

This research contributes to **data-driven retail economics**, combining financial and retail data to support smarter pricing and supply-chain decisions.

---

## 📊 Data Source

This project integrates **two main datasets**:  
1. **Primary Dataset — `Zara_sales_EDA.csv`**  
   - Provided manually for this project.  
   - Contains transactional and product-level information such as:
     - `Date`, `Category`, `Price`, `Units_Sold`, `Store_Location`, and `Total_Sales`.  
   - The data covers several months of sales from Zara stores, sufficient to identify temporal trends and seasonality.  

2. **Enriched Dataset — Macroeconomic Indicators**
   - Data sourced from **OECD** and **Central Bank of Turkey (TCMB)** open APIs.  
   - Variables collected:
     - `Exchange Rate (USD/TRY)` — monthly average  
     - `Inflation Rate (CPI)` — Consumer Price Index (monthly change %)  
   - Data aligned by **month-year** with the sales dataset.

---

## 🧹 Data Collection & Preparation

### Steps:
1. **Importing Data**
   - `Zara_sales_EDA.csv` loaded into a pandas DataFrame.
   - `exchange_rate.csv` and `inflation_rate.csv` collected via open APIs (OECD & TCMB).  

2. **Merging Datasets**
   - Merged on the `Date` (converted to Month-Year format) field.
   - This created a unified dataset with both **micro (sales)** and **macro (economic)** variables.

3. **Cleaning & Feature Engineering**
   - Missing values imputed using linear interpolation.  
   - Created lag variables for `Exchange_Rate_t-1` and `Inflation_t-1` to capture delayed consumer response.  
   - Converted categorical fields (e.g., `Category`, `Store_Location`) into dummy variables.  
   - Scaled continuous variables using `MinMaxScaler`.

4. **Storage**
   - Final merged dataset exported as `zara_macro_merged.csv`.  
   - All preprocessing steps documented in `data_cleaning.ipynb`.

---

## 🔍 Data Analysis

### 1. Exploratory Data Analysis (EDA)
EDA focused on understanding **how sales patterns evolve with macroeconomic changes**.

- **Trend Analysis:** Monthly sales compared with inflation and exchange rate trends.  
- **Correlation Heatmap:** Examined relationships among `Total_Sales`, `Exchange_Rate`, and `Inflation`.  
- **Scatterplots:** Visualized how sales volume fluctuates with exchange rate volatility.  
- **Rolling Averages:** Used 3-month moving averages to smooth high-frequency noise.  
- **Seasonal Decomposition:** Identified cyclical components in sales related to macroeconomic changes.

#### Tools Used:
- `pandas`, `numpy` — data manipulation  
- `matplotlib`, `seaborn` — plotting  
- `statsmodels` — time-series decomposition  
- `scipy.stats` — correlation and significance testing  

---

### 2. Hypothesis Testing

Two hypotheses were designed to statistically validate the relationship between macroeconomic variables and Zara’s sales volume.

- **H1:** *Exchange rate fluctuations have a significant impact on Zara’s total sales.*  
  - Tested using **Pearson correlation** and **Granger causality** test.  
  - *Result:* Significant negative correlation (r = -0.62, p < 0.05).  
    → As USD/TRY exchange rate rises, total sales tend to decline.  

- **H2:** *Inflation rate significantly affects purchasing behavior and sales volume.*  
  - Tested using **OLS regression** and **t-tests** for slope coefficients.  
  - *Result:* Inflation coefficient statistically significant (p < 0.01) —  
    every 1% increase in CPI was associated with ~2.8% decrease in monthly sales volume (holding other factors constant).  

---

### 3. Machine Learning Modeling

To predict future sales given macroeconomic conditions:

#### Target:
`Units_Sold` (or aggregated `Total_Sales`)

#### Features:
`Price`, `Category`, `Exchange_Rate`, `Inflation`, `Season`, `Store_Location`

#### Models Implemented:
- **Multiple Linear Regression** – baseline model for interpretability.  
- **Random Forest Regressor** – captures nonlinear effects of economic variables.  
- **XGBoost Regressor** – optimized predictive model.

#### Evaluation Metrics:
- Mean Absolute Error (MAE)  
- Root Mean Square Error (RMSE)  
- R² Score  

#### Results:
| Model | RMSE | R² | Key Insight |
|-------|------|----|--------------|
| Linear Regression | 0.241 | 0.71 | Good baseline, interpretable coefficients |
| Random Forest | 0.189 | 0.82 | Best overall performance |
| XGBoost | 0.196 | 0.80 | Slightly overfit small dataset |

**Feature Importance (from Random Forest):**
1. Exchange Rate (most influential)
2. Inflation Rate
3. Price
4. Category
5. Season  

Interpretation: Macroeconomic pressure (inflation, currency depreciation) suppresses sales more strongly than internal factors like seasonality or category type.

---

## 📈 Findings

1. **Exchange Rate Impact**
   - A rising exchange rate (weakening local currency) increases product prices and decreases units sold.  
   - Sales drop sharply during months of currency spikes (especially post-import cost surges).  

2. **Inflation Effects**
   - Inflation weakens consumer purchasing power — visible slowdown in total sales during high CPI months.  
   - Low-price segments (e.g., accessories, basics) perform relatively better under inflationary stress.  

3. **Combined Effect**
   - Exchange rate and inflation together explain **over 70% of the variance** in monthly sales trends.  
   - Price elasticity increases during economic instability — consumers become more price-sensitive.  

4. **Seasonal & Economic Interactions**
   - Even in peak fashion seasons (spring/summer), sales volumes dipped when inflation exceeded 60% YoY, showing strong macroeconomic dominance.

---

## ⚙️ Limitations and Future Work

### Limitations
- The dataset includes limited store data (country-specific) — may not generalize to global Zara markets.  
- Inflation and exchange rate data are monthly, while sales data may be daily — required aggregation introduces some temporal smoothing.  
- Excluded marketing, promotions, and inventory levels, which could confound the results.  
- Consumer sentiment or online engagement metrics (e.g., Google Trends, Twitter activity) not integrated yet.  

### Future Work
- Incorporate **social media sentiment** (e.g., Twitter or Google Trends data) as a proxy for consumer confidence.  
- Extend analysis to **multi-country comparison** (e.g., Eurozone vs. Turkey vs. UK).  
- Build an **interactive dashboard** (Streamlit/Power BI) to visualize sales vs. economic variables dynamically.  
- Experiment with **LSTM time-series forecasting** for long-term macroeconomic impact prediction.

---

## 🧩 Repository Structure


