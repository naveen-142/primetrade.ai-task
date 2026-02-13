# 📊 Trader Performance vs Market Sentiment  
### Data Science / Analytics Assignment – Primetrade.ai


## 📌 Overview

This project explores how Bitcoin market sentiment (Fear & Greed Index) relates to trader behavior and performance on Hyperliquid.

The objective is to understand:

- Whether trader profitability changes across sentiment regimes  
- How trading behavior shifts during Fear vs Greed  
- Which trader segments are more resilient  
- What practical trading rules can be derived from the analysis  

All analysis is conducted at a **daily trader-level granularity**.


## 📁 Datasets

### 1️⃣ Bitcoin Market Sentiment Dataset
Fields:
- Timestamp (Unix)
- Classification  
  - Extreme Fear  
  - Fear  
  - Neutral  
  - Greed  
  - Extreme Greed  

### 2️⃣ Hyperliquid Historical Trader Data
Includes:
- Account  
- Execution Price  
- Size (USD)  
- Side (Buy/Sell)  
- Closed PnL  
- Timestamp (IST)  
- Fee  
- Trade identifiers  


## ⚙️ Methodology

### Step 1 — Data Cleaning & Alignment

- Removed duplicate rows  
- Converted Unix timestamps to `datetime`  
- Normalized timestamps to daily level  
- Aligned trade data with corresponding daily sentiment classification  
- Verified date overlap before merging  

All analysis is based on a correctly merged daily dataset.

### Step 2 — Feature Engineering

Constructed daily trader-level metrics:

- **Daily PnL per account**
- **Win rate (proportion of profitable trades)**
- **Average trade size (USD)**
- **Trade frequency (trades per day)**
- **Long ratio (Buy bias)**

These features allowed both performance and behavioral analysis.


## 📊 Part B — Analysis & Findings

### 1️⃣ Performance by Sentiment Regime

| Regime | Mean PnL | Median PnL | Std Dev |
|--------|----------|------------|---------|
| Fear | Highest mean | Lower median | Highest volatility |
| Extreme Greed | High mean | Highest median | High volatility |
| Neutral | Lower mean | Moderate median | Lowest volatility |

**Key Observations:**

- Fear regimes produce higher average PnL but also the highest volatility.
- Extreme Greed shows the highest median PnL, suggesting broader profitability distribution.
- Neutral markets are more stable but less profitable.

This indicates that emotional regimes amplify both opportunity and risk, while neutral markets dampen both.


### 2️⃣ Behavioral Shifts Across Regimes

During Fear regimes:

- Trade frequency increases significantly
- Average trade size increases
- Long bias increases
- Win rate declines

This suggests traders become more aggressive in fearful conditions but are not rewarded proportionally.

During Extreme Greed:

- Win rates improve
- Activity levels moderate
- Profitability appears more evenly distributed

This suggests strong positive momentum environments may be structurally easier to trade.


### 3️⃣ Trader Segmentation Insights

#### 🔹 Frequent vs Infrequent Traders
- Frequent traders show more stable performance across regimes.
- Infrequent traders exhibit larger PnL swings and higher regime sensitivity.

#### 🔹 Consistent vs Inconsistent Traders
- Consistent traders experience lower volatility across regimes.
- Inconsistent traders are disproportionately affected during emotional regimes.

Performance dispersion expands significantly during Fear and Extreme Greed.


## 📈 Optional Predictive Modeling

An exploratory Random Forest classifier was trained to predict trader profitability using:

- Trade frequency  
- Average position size  
- Long ratio  
- Sentiment classification  

The model achieved approximately **80% accuracy** on held-out data.

However:
- This was an exploratory exercise.
- Further time-aware validation would be required for production reliability.
- The objective was to assess signal strength, not to deploy a trading model.


## 🧠 Strategic Recommendations

### ✅ Rule 1 — Risk Compression During Fear

During Fear and Extreme Fear regimes:

- Reduce position sizing  
- Limit excessive trade frequency  
- Avoid aggressive long bias  

Rationale: Fear regimes correlate with higher volatility and lower win rates.


### ✅ Rule 2 — Controlled Scaling During Extreme Greed

During Extreme Greed regimes:

- Allow moderate scaling for consistent traders  
- Encourage participation in strong directional moves  
- Maintain exposure caps for volatile accounts  

Rationale: Extreme Greed shows broader profitability distribution and improved median outcomes.



## 🛠 Tech Stack

- Python  
- Pandas  
- NumPy  
- Matplotlib / Seaborn  
- Scikit-learn  

## 🏁 Conclusion

Market sentiment meaningfully influences trader behavior and performance dispersion.

Fear regimes drive higher activity and larger position sizes but lower win rates, suggesting risk amplification behavior. Extreme Greed regimes exhibit stronger median profitability and broader participation in gains.

Incorporating sentiment-aware exposure controls may improve risk-adjusted performance and reduce drawdowns.
