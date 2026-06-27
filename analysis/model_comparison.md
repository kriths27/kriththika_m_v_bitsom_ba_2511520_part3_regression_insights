# Model Comparison — Simple vs. Multiple Regression
**Dependent Variable:** `monthly_sales`  
**Dataset:** `business_regression_data.xlsx` | **n = 320**

---

## Comparison Table

| Metric | SLR-1: Marketing Spend | SLR-2: Footfall | MLR: Full Model |
|---|---|---|---|
| **R-Squared** | 0.1672 | 0.7363 | **0.8309** |
| **Adj. R-Squared** | 0.1646 | 0.7355 | **0.8255** |
| **F-Statistic** | 63.86 | 887.85 | **151.88** |
| **F-Stat P-Value** | 0.000000 | 0.000000 | **0.000000** |
| **RMSE** | ₹94,846 | ₹53,374 | **₹43,352** |
| **AIC** | 8244.52 | 7876.56 | **7752.28** |
| **No. Predictors** | 1 | 1 | 10 |

---

## SLR-1: monthly_sales ~ marketing_spend

### Equation
```
monthly_sales = 560,777.35 + 2.1296 × marketing_spend
```

### Interpretation
- **Intercept (₹560,777.35):** Estimated baseline sales when marketing spend is ₹0. This is a mathematical anchor — practically, zero marketing spend is not realistic.
- **Coefficient (2.1296):** For every ₹1 increase in marketing spend, monthly_sales increases by approximately ₹2.13. This is a positive relationship.
- **R² = 0.1672:** Marketing spend alone explains only **16.7%** of variance in monthly sales — weak explanatory power.
- **P-Value = 0.000000:** Statistically significant at α = 0.05.

### Business Meaning
Marketing spend has a measurable but limited impact on sales. The low R² suggests many other factors drive sales beyond marketing alone.

---

## SLR-2: monthly_sales ~ footfall

### Equation
```
monthly_sales = 446,410.58 + 35.6780 × footfall
```

### Interpretation
- **Intercept (₹446,410.58):** Baseline sales when footfall is 0 (theoretical reference).
- **Coefficient (35.6780):** Each additional visitor is associated with ₹35.68 in additional monthly sales.
- **R² = 0.7363:** Footfall explains **73.6%** of variance in sales — stronger than marketing spend alone.
- **P-Value = 0.000000:** Statistically significant.

### Business Meaning
Footfall is a better single predictor of monthly sales than marketing spend. This suggests that physical store traffic is more directly tied to revenue than marketing investment alone.

---

## MLR: monthly_sales ~ 7 numeric predictors + 3 store-type dummies

### R-Squared Improvement
| Model | R² | Adj. R² | Gain vs. Best SLR |
|---|---|---|---|
| SLR-1 | 0.1672 | 0.1646 | — |
| SLR-2 | 0.7363 | 0.7355 | — |
| **MLR** | **0.8309** | **0.8255** | **+9.5pp** |

The MLR achieves **83.1% explanatory power**, a significant improvement over either simple model.

### Significant Predictors in MLR (p < 0.05)

| Predictor | Coefficient | P-Value | Direction |
|---|---|---|---|
| Marketing Spend (₹) | 1.16 | 0.000000 | ↑ Positive |
| Monthly Footfall (visitors) | 28.07 | 0.000000 | ↑ Positive |
| Staff Count | 3,031.49 | 0.015864 | ↑ Positive |
| Inventory Availability % | 3,176.72 | 0.000000 | ↑ Positive |
| Customer Rating (1-5) | 13,280.97 | 0.005668 | ↑ Positive |
| Holiday Month (0/1) | 13,035.53 | 0.048764 | ↑ Positive |
| Store Type: High Street vs Residential | 19,551.42 | 0.001235 | ↑ Positive |
| Store Type: Airport vs Residential | 41,282.91 | 0.000014 | ↑ Positive |
| Store Type: Mall vs Residential | 29,336.94 | 0.000013 | ↑ Positive |


### Non-Significant Predictors (p ≥ 0.05)

| Predictor | Coefficient | P-Value |
|---|---|---|
| Intercept (Baseline) | 37,032.33 | 0.446808 |
| Avg Discount % (0-1) | -68,113.21 | 0.059403 |


---

## Key Takeaway

The **Multiple Regression model is clearly superior** — it captures 83.1% of sales variance versus 73.6% for the best simple model. The improvement comes from accounting for footfall, discount behaviour, inventory, customer rating, and store type simultaneously.
