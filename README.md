Yusuf Arif Özkuttaş 32097 Section D
#  Geopolitical Risk and Financial Assets – DSA210 Project

## Project Overview

This project explores how **global geopolitical risk (GPR)** influences the behavior of key financial assets — specifically **gold** and **Bitcoin**. Using three datasets that capture market prices and geopolitical risk indices, the project investigates whether geopolitical uncertainty affects volatility, returns, and safe-haven dynamics.

By integrating cryptocurrency, commodity, and macroeconomic data, this study aims to bridge economic theory with data science practice, offering insights into how traditional and digital assets respond under global stress conditions.

---

## Objectives

1. **Quantify Risk–Return Relationships**  
   Measure how fluctuations in the Geopolitical Risk Index (GPR) influence the daily returns and volatility of Bitcoin and gold.

2. **Compare Asset Sensitivity BUNUÇIKARABİLİRSİN!!!**  
   Evaluate whether gold or Bitcoin behaves more like a “safe-haven” asset during periods of elevated geopolitical tension.

3. **Predict Volatility Using Machine Learning**  
   Build models that use GPR and lagged market indicators to predict daily volatility.

4. **Evaluate Market Dynamics During Crises**  
   Identify whether Bitcoin’s response to global uncertainty has evolved in recent years compared to gold.

---

## Motivation

Global markets often react sharply to political instability, wars, and global uncertainty. Gold is historically known as a stable store of value, while Bitcoin’s role as a potential “digital gold” is still being debated.  

Understanding how these assets react to **geopolitical stress** provides valuable information for:
- **Investors**, seeking portfolio hedging strategies.  
- **Economists**, analyzing market psychology and capital flow.  
- **Policy-makers**, assessing how global shocks impact new financial systems.

This project merges **macroeconomic theory and modern data analytics** to provide a quantitative view of these relationships.

---

## Dataset

This project integrates three real-world datasets:

### **1. btcusd_1-min_data.csv**
- **Description:** Minute-level Bitcoin–USD price data, aggregated to daily averages.
- **Key Features:**
  - Open, Close, High, Low prices  
  - Timestamp  
  - Trading volume  
- **Purpose:** Measure Bitcoin daily returns and volatility.

### **2. goldstock v2.csv**
- **Description:** Daily or weekly gold price index data.
- **Key Features:**
  - Gold closing prices  
  - Market index indicators  
- **Purpose:** Provide traditional safe-haven benchmark.

### **3. data_gpr_export.xls**
- **Description:** Global Geopolitical Risk (GPR) Index by Caldara & Iacoviello (Federal Reserve Board).
- **Key Features:**
  - Monthly geopolitical risk scores  
  - Global aggregation from international news coverage  
- **Source:** [https://www2.bc.edu/matteo-iacoviello/gpr.htm](https://www2.bc.edu/matteo-iacoviello/gpr.htm)

---

## Hypotheses TEK HYPOTHESİS YAP!!!1

1. **Geopolitical Risk and Gold Prices**  
   - **H₀:** GPR levels have no significant effect on gold prices.  
   - **H₁:** Increases in GPR are associated with higher gold prices.  
   *(Tested via Pearson correlation and t-test)*

2. **Geopolitical Risk and Bitcoin Volatility**  
   - **H₀:** GPR has no significant effect on Bitcoin volatility.  
   - **H₁:** Rising GPR increases Bitcoin volatility.  
   *(Tested via variance tests and GARCH models)*

3. **Safe-Haven Comparison**  
   - **H₀:** There is no difference between gold and Bitcoin’s reactions to geopolitical risk.  
   - **H₁:** Gold reacts more strongly and consistently to GPR changes than Bitcoin.  
   *(Tested via two-sample t-tests and rolling correlation analysis)*

4. **Predictive Power of GPR**  
   - **H₀:** Including GPR in machine learning models does not improve volatility prediction.  
   - **H₁:** Adding GPR significantly improves volatility prediction accuracy.  
   *(Evaluated via Random Forest/XGBoost model performance)*

---

## Analysis Plan

1. **Data Cleaning and Preprocessing**  
   - Convert timestamps to daily frequency  
   - Handle missing values and align datasets by date  
   - Calculate daily returns and volatility measures  

2. **Exploratory Data Analysis (EDA)**  
   - Visualize trends and distributions  
   - Compute rolling correlations (GPR vs. BTC/Gold)  
   - Identify major spikes linked to global events  

3. **Statistical Testing**  
   - Correlation and hypothesis tests for each H₀/H₁  
   - Granger causality tests for directional relationships  

4. **Machine Learning Prediction**  
   - Train regression models (Random Forest, XGBoost)  
   - Evaluate prediction performance (MAE, R²)  
   - Compare baseline vs. GPR-augmented models  

5. **Visualization and Interpretation**  
   - Time-series plots and volatility heatmaps  
   - Feature importance rankings  
   - Rolling correlation and crisis-period comparison  

---

## Findings and Insights

Preliminary analysis suggests that:
- Gold consistently rises during geopolitical crises, confirming its safe-haven nature.  
- Bitcoin reacts more to **market sentiment** and shows **increased volatility**, but not necessarily positive returns.  
- The predictive value of GPR for Bitcoin volatility is moderate — useful but less stable than for gold.  
- The relationship appears **time-dependent**, strengthening during global crises.

