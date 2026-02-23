# Marketing A/B Testing & Conversion Optimization

## Project Overview

This project analyzes a digital marketing campaign using a dataset of over 588,000 customer interactions from a Kaggle competition. The analysis combines inferential statistics, machine learning, and time‑series forecasting to move beyond historical reporting and provide actionable insights for optimizing trade spend and supply chain planning.

**Dataset:** [Marketing A/B Testing on Kaggle](https://www.kaggle.com/datasets/faviovaz/marketing-ab-testing)

## Business Questions

1. Did the promotional ad campaign produce a statistically significant lift in conversions compared to the baseline PSA (public service announcement)?
2. How do the day of the week and the hour of the day influence conversion probability?
3. At what point does repeated ad exposure become ineffective, and what is the optimal frequency?
4. Can we forecast future conversion rates to support proactive inventory and promotional decisions?

## Technical Stack

- **Language:** Python 3.13
- **Data Manipulation:** pandas, numpy
- **Statistical Analysis:** scipy, statsmodels (Two‑Proportion Z‑Test, Chi‑Square Test, Simple Exponential Smoothing)
- **Machine Learning:** scikit‑learn (Logistic Regression)
- **Visualization:** matplotlib, seaborn

## Key Insights & Strategic Recommendations

### 1. The Ad Campaign Significantly Lifts Conversions

- **Result:** The ad group achieved a conversion rate of 2.55%, while the PSA (control) group converted at 1.79%. This represents a relative lift of **43.1%**.
- **Statistical Proof:** A two‑proportion Z‑test returned a p‑value of `1.71e-13`, far below the 0.05 threshold. The 95% confidence intervals for the two groups do not overlap ([2.51%, 2.60%] for ad vs. [1.62%, 1.96%] for PSA), confirming that the difference is not due to random chance.
- **Recommendation:** Continue investing in the ad campaign; its effect is both statistically and practically significant.

### 2. “Broad and Shallow” Marketing Fails – Deep Retargeting Wins

- **Ad Fatigue Analysis:** Conversion rates increase dramatically with ad frequency:
  - 1‑5 ads: 0.25%
  - 6‑10 ads: 0.44%
  - 11‑20 ads: 1.04%
  - 21‑50 ads: 2.92%
  - 50+ ads: **13.46%**
- **Insight:** Users do not experience traditional fatigue; instead, they require high repetition to convert. The highest returns come from users who see the ad more than 20 times.
- **Recommendation:** Reallocate budget from broad, low‑frequency campaigns to aggressive retargeting, focusing on pushing high‑intent users past the 20‑ad threshold.

### 3. Weekend Advertising Yields Negative Returns

- **Predictive Modeling (Logistic Regression):** Coefficients indicate the strongest positive predictors of conversion are **Monday (+0.403)** and **Tuesday (+0.329)**. Saturday is a negative predictor (**-0.102**), meaning that showing ads on this day actually lowers the chance of conversion. The PSA group coefficient (**-0.294**) further validates that the ad itself drives conversions.
- **Recommendation:** Concentrate ad spend on Mondays and Tuesdays, and pause campaigns on Saturdays to avoid diminishing returns.

### 4. Stable Short‑Term Forecast Averts Supply Chain Surprises

- **Time‑Series Forecasting:** Using Simple Exponential Smoothing on 28 days of simulated daily data, a 7‑day forecast projects a stable average conversion rate of approximately **2.5%**. Model accuracy metrics: MAE = 0.34, RMSE = 0.48.
- **Recommendation:** Maintain standard inventory levels; no emergency adjustments are required until the next promotional cycle.

## Repository Structure

```
📁 images/
    ├── ab_test_baseline.png          # Baseline conversion rates (ad vs. psa)
    ├── ConversionRateDay.png          # Conversion rate by day of week
    ├── ad_fatigue_chart.png           # Ad frequency vs. conversion rate
    └── time_series_forecast.png       # 7‑day forecast plot
📄 promotion_ab_test_fin.ipynb          # Complete Jupyter Notebook with analysis
📄 README.md                             # This file
```

---
*Author: Mahfoud Bouad*
