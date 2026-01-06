# Impact of Extreme Gold Price Movements on NSE Stock Intraday Returns

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green)
![Status](https://img.shields.io/badge/Project-Completed-success)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 📌 Project Overview

This project analyzes how **NSE-listed stocks behave on the trading day following extreme gold price movements**.  
Gold is treated as a **macro-level risk and sentiment indicator**, and the study focuses on identifying stocks that consistently outperform after such extreme gold movements.

The analysis is conducted **year-by-year**, strictly avoiding look-ahead bias, and is designed to scale to **very large datasets (~750 MB)** using memory-efficient processing.

---

## 🎯 Objective

To answer the question:

> *How do NSE stocks react intraday on days following extreme gold price movements, and which stocks consistently perform best during such periods?*

---

## 🧠 Key Concepts Used

- Intraday stock returns  
- Percentile-based definition of “extreme” gold movements  
- Lagged (next-day) reaction analysis  
- Look-ahead bias avoidance  
- Large-scale data handling using chunked processing  
- Year-wise and percentile-wise stock ranking  

---

## 📊 Data Description

### Gold Data
- Daily gold spot prices
- Used to compute daily gold returns
- Extreme movements defined using **Top 95%** and **Bottom 5%** percentiles of historical returns

### Stock Data
- NSE daily stock prices (Open, Close)
- Dataset size: ~750 MB
- Millions of rows across multiple years and companies

> ⚠️ **Raw datasets are not included in this repository** due to size and licensing considerations.

---

## ⚙️ Methodology (High-Level)

1. **Compute Gold Returns**
   - Daily percentage returns from gold spot prices

2. **Define Extreme Gold Days**
   - For each year, calculate gold return percentiles using all data available *up to that year*
   - Apply **previous-year thresholds** to classify extreme gold days in the current year

3. **Identify Reaction Days**
   - Analyze stock intraday returns on the **next trading day** following extreme gold movements

4. **Compute Company-Level Averages**
   - Average intraday returns per stock, per year, separately for:
     - Top Gold days
     - Bottom Gold days

5. **Percentile-Based Ranking**
   - Identify stocks in the **Top 5%, 4%, 3%, 2%, and 1%**
   - Done separately for each year and extreme gold category

---

## 🧪 Key Design Decisions

- **Chunk-wise CSV processing** used to handle large stock datasets efficiently
- **Symbol-based analysis** preferred over full company names for memory efficiency
- Initial periods without sufficient historical data are excluded by design
- Reaction-day counts tracked to assess statistical robustness

---

## 📈 Visualizations Included

- Evolution of extreme gold return thresholds over time  
- Frequency of extreme gold days per year  
- Distribution of stock intraday returns following extreme gold movements  
- Top 5% Stock Performance After Extreme Gold Movements

Each visualization is included to **support interpretation**, not for decoration.

---

## 📌 Key Takeaways

- Stock reactions to extreme gold movements are heterogeneous
- Some stocks consistently outperform during periods of heightened macro stress
- Results vary significantly across years, highlighting regime dependence
- Careful handling of historical information is critical to avoid misleading conclusions

## 📜 License

This project is released under the MIT License.

## 👤 Author

- Gautam Sharma
- B.Tech CSE | Machine Learning & Data Science
**Focus areas**: time-series analysis, large-scale data processing, applied financial analytics