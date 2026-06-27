# Part 3: Regression-Based Business Insights & Model Interpretation

**Student:** Kriththika M V | **ID:** `bitsom_ba_2511520`
**Tool Stack:** Python 3 (pandas, statsmodels, scipy, xlsxwriter, matplotlib)

---

## Problem Statement

An Indian retail chain with **80 stores** across 4 regions and 4 store types wants to understand what drives monthly sales. Data covers January–April 2025 (320 store-month observations across 14 variables). The goal: build regression models to identify significant predictors of `monthly_sales`, compare model performance, and deliver actionable business recommendations.

---

## Repository Structure

```
├── data/
│   └── business_regression_data.xlsx
├── analysis/
│   ├── regression_workbook.xlsx  ← 5-sheet OLS output workbook
│   ├── model_comparison.md       ← SLR vs MLR R², equations, interpretations
│   └── residual_analysis.md      ← Top 5 positive/negative residuals + meaning
├── outputs/
│   ├── regression_summary.xlsx   ← Clean comparison table of all 3 models
│   ├── final_recommendation.md   ← Actionable leadership memo
│   └── model_equations.md        ← Formulas, all coefficients, dummy reference categories
├── screenshots/
│   ├── simple_regression_output.png    ← Scatter + residuals for SLR-1 & SLR-2
│   ├── multiple_regression_output.png  ← Coef plot, actual vs predicted, p-values
│   ├── residuals_preview.png           ← QQ plot, histogram, outlier bar chart
│   └── model_comparison_preview.png    ← R², RMSE, AIC comparison + correlations
└── README.md
```

---

## Dataset Description

| Attribute | Value |
|---|---|
| Source file | `business_regression_data.xlsx` |
| Rows | 320 (80 stores × 4 months) |
| Columns | 14 |
| Dependent Variable | `monthly_sales` |
| Categorical Variables | `store_type` (4 levels), `region` (4 levels) |
| Missing Values | `competitor_distance_km` (6), `customer_rating` (8) → imputed with median |

---

## Dummy Variables Created

| Variable | Reference Category | Dummies Created |
|---|---|---|
| `store_type` | **Residential** (baseline) | `store_type_High_Street`, `store_type_Airport`, `store_type_Mall` |
| `region` | **East** (baseline) | `region_North`, `region_South`, `region_West` |

> All dummy coefficients in the MLR represent the *average difference in monthly_sales* vs. the reference category, holding all other variables constant.

---

## Models Built

### SLR-1: monthly_sales ~ marketing_spend

```
monthly_sales = 635,682.79 + 2.1296 × marketing_spend
```

| Metric | Value |
|---|---|
| R-Squared | 0.1672 |
| Coefficient | 2.1296 (each ₹1 in marketing → ₹2.13 in sales) |
| P-Value | < 0.0001 ✅ Significant |
| Interpretation | Weak explanatory power alone — only 16.7% of variance explained |

---

### SLR-2: monthly_sales ~ footfall

```
monthly_sales = 446,038.87 + 35.678 × footfall
```

| Metric | Value |
|---|---|
| R-Squared | **0.7363** |
| Coefficient | 35.68 (each additional visitor → ₹35.68 in monthly sales) |
| P-Value | < 0.0001 ✅ Significant |
| Interpretation | Strong single predictor — footfall alone explains 73.6% of variance |

---

### MLR: monthly_sales ~ 7 numeric + 3 store-type dummies

| Metric | Value |
|---|---|
| **R-Squared** | **0.8309** |
| **Adj. R-Squared** | **0.8255** |
| **F-Statistic** | **151.88** (p < 0.0001) |
| **RMSE** | ₹42,766 |
| Predictors | marketing_spend, footfall, avg_discount_pct, staff_count, inventory_availability_pct, customer_rating, holiday_flag + 3 store-type dummies |

---

## Model Comparison Summary

| Metric | SLR-1 | SLR-2 | **MLR** |
|---|---|---|---|
| R-Squared | 0.1672 | 0.7363 | **0.8309** |
| Adj. R-Squared | 0.1645 | 0.7349 | **0.8255** |
| RMSE | ₹94,840 | ₹53,428 | **₹42,766** |
| F-Statistic | 63.67 | 885.6 | **151.88** |
| AIC | 8,252 | 7,953 | **7,758** |
| **Winner** | ❌ | ❌ | **✅ Best** |

---

## Top Residuals (MLR)

| Type | Store | Region | Store Type | Residual |
|---|---|---|---|---|
| ↑ Most underestimated | STR-1030 | West | Residential | +₹103,317 |
| ↑ 2nd | STR-1028 | East | Mall | +₹101,709 |
| ↓ Most overestimated | STR-1017 | West | High Street | -₹157,212 |
| ↓ 2nd | STR-1023 | South | Mall | -₹126,607 |

---

## VIF Results (Multicollinearity)

| Feature | VIF | Risk |
|---|---|---|
| footfall | 6.48 | 🟡 Moderate |
| staff_count | 6.46 | 🟡 Moderate |
| All others | < 2 | 🟢 Low |

No variables exceed VIF = 10 — no severe multicollinearity.

---

## Key Business Findings

1. **Footfall is the #1 driver** — explains 73.6% of sales on its own; each visitor = ₹35.68 in revenue
2. **Store type matters significantly** — different store types show meaningfully different baselines after controlling for footfall and marketing
3. **Inventory availability is actionable** — every 1% improvement → measurable sales uplift
4. **Marketing spend has diminishing returns** — small coefficient relative to footfall; effectiveness depends on how it converts to foot traffic
5. **Customer rating is a leading indicator** — higher-rated stores consistently outperform

---

## Critical Note: Correlation ≠ Causation

All regression findings show statistical **associations** only. Causal claims require controlled A/B experiments. Do not infer that investing ₹X in marketing *will* yield exactly ₹Y in sales — the model captures tendencies, not guarantees.

---

## Screenshots

| File | Description |
|---|---|
| `simple_regression_output.png` | Scatter + residuals for SLR-1 (marketing) and SLR-2 (footfall) |
| `multiple_regression_output.png` | Coefficient plot, actual vs predicted, p-value chart, store-type boxplot |
| `residuals_preview.png` | Residuals vs fitted, QQ plot, histogram, top 10 outlier bars |
| `model_comparison_preview.png` | R², RMSE, AIC comparison bars + correlation heatmap |

