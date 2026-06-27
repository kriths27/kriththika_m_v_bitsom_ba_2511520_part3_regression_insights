# Final Recommendation — Regression-Based Business Insights
**To:** Senior Leadership & Operations Team   
**Date:** 27 June 2026  
**Based on:** Multiple Linear Regression (R² = 0.8309, n = 320 store-months)

---

## Executive Summary

A regression analysis of **320 store-month records** across 80 stores and 4 months was conducted to identify the strongest drivers of monthly sales. The best-fit Multiple Regression model explains **83.1%** of sales variance (Adjusted R² = 0.8255) and is statistically significant (F = 151.88, p < 0.001).

---

## What Leadership Should Focus On

### 1. 🏪 Store Type Strategy (Strongest Structural Driver)
- **Store Type: Airport vs Residential**: coefficient = ₹41,283/month (+), p = 0.0000  
- **Store Type: Mall vs Residential**: coefficient = ₹29,337/month (+), p = 0.0000  
- **Store Type: High Street vs Residential**: coefficient = ₹19,551/month (+), p = 0.0012  

**Action:** Prioritise capital investment and new store openings in the highest-performing store type category. Review whether Residential stores need repositioning or operational support.

### 2. 👟 Footfall is the Engine of Sales
- Coefficient: ₹28.07 per additional visitor (p = 0.0000)
- **Action:** Invest in footfall-driving initiatives — window displays, localised marketing, partnerships with nearby businesses. A 10% footfall increase → approximately ₹18,426 additional monthly sales per store.

### 3. 📦 Inventory Availability Directly Impacts Revenue
- Coefficient: ₹3,177 per 1% improvement in availability
- **Action:** Push inventory availability above 90% at all stores. Every stockout is a missed sale. Implement demand-forecasting tools for top-20 SKUs.

### 4. ⭐ Customer Rating as a Leading Indicator
- Coefficient: ₹13,281 per 1-star improvement
- **Action:** Implement systematic rating improvement programs (post-purchase NPS, service training) — ratings are associated with meaningful sales upside.

### 5. 📅 Holiday Months: Prepare Proactively
- Coefficient: ₹13,036 uplift in holiday months
- **Action:** Pre-stock inventory, increase staffing, and allocate higher marketing budgets for holiday months to capture this seasonal uplift.

---

## What NOT to Over-Interpret

1. **Marketing Spend (p = 0.0000):** Marketing spend is significant but its coefficient is small. This does not mean marketing doesn't work — it may reflect diminishing returns or the fact that high-spend stores are in challenging locations.
2. **Average Discount % (p = 0.0594):** High discount rates are associated with lower net sales. However, causation is unclear — struggling stores may be discounting more. Do not reduce discounts without deeper analysis.
3. **R² = 0.8309:** The model explains 83.1% of variance. The remaining 16.9% is driven by factors not in the dataset (local competition, weather, management quality, etc.).

---

## Regression Association vs. Causation

> ⚠️ **Critical Reminder:** These regression results show *associations*, not proven causal relationships.

| What the regression shows | What it does NOT show |
|---|---|
| Footfall is correlated with higher sales | That increasing footfall will *necessarily* increase sales |
| Airport stores have different sales levels | That switching to airport locations will improve performance |
| Customer rating correlates with sales | That improving ratings *causes* sales to increase |

To establish causation, conduct **randomised controlled experiments** (e.g., test a footfall-driving campaign in 20 stores vs. 20 control stores and measure the difference).

---

## Limitations

1. Only 4 months of data (Jan–Apr 2025) — seasonal patterns and full-year dynamics are not captured
2. Store-level fixed effects (management quality, local market structure) are unaccounted for
3. Missing `competitor_distance_km` for 6 stores — imputed with median; may slightly bias coefficients
4. No interaction terms tested (e.g., does marketing ROI differ by store type?)
5. Panel data structure (repeated store observations) may require mixed-effects models for unbiased standard errors

