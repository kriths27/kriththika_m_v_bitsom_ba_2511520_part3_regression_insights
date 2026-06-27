# Model Equations, Coefficients & Reference Categories

---

## Dummy Variable Reference Categories

| Variable | Dummies Created | **Reference Category** | Explanation |
|---|---|---|---|
| `store_type` | High Street, Airport, Mall | **Residential** | Most common store type; all dummies measure deviation from Residential performance |
| `region` | North, South, West | **East** | Baseline region; regional dummies are included in MLR for completeness |

> **How to read dummy coefficients:** The coefficient on `store_type_Mall`, for example, represents the *average difference in monthly_sales* between a Mall store and a Residential store, holding all other variables constant.

---

## Model 1 — Simple Linear Regression: marketing_spend

### Equation
```
monthly_sales = 560,777.35
              + 2.129575 × marketing_spend
```

| Term | Value | Interpretation |
|---|---|---|
| Intercept | ₹560,777.35 | Baseline sales with zero marketing spend (theoretical anchor) |
| `marketing_spend` coefficient | 2.129575 | Each ₹1 in marketing → ₹2.1296 in sales |
| R² | 0.1672 | Model explains 16.7% of sales variance |
| P-value (coefficient) | 0.000000 | ✅ Significant at α=0.05 |

---

## Model 2 — Simple Linear Regression: footfall

### Equation
```
monthly_sales = 446,410.58
              + 35.678031 × footfall
```

| Term | Value | Interpretation |
|---|---|---|
| Intercept | ₹446,410.58 | Baseline sales with zero footfall (theoretical anchor) |
| `footfall` coefficient | 35.678031 | Each additional visitor → ₹35.6780 in monthly sales |
| R² | 0.7363 | Model explains 73.6% of sales variance |
| P-value (coefficient) | 0.000000 | ✅ Significant at α=0.05 |

---

## Model 3 — Multiple Linear Regression: Full Model

### Equation
```
monthly_sales = 37,032.33
              + 1.160161   × marketing_spend
              + 28.068198           × footfall
              + -68,113.21  × avg_discount_pct
              + 3,031.49        × staff_count
              + 3,176.72 × inventory_availability_pct
              + 13,280.97   × customer_rating
              + 13,035.53       × holiday_flag
              + 19,551.42 × store_type_High_Street
              + 41,282.91     × store_type_Airport
              + 29,336.94        × store_type_Mall
```

### Full Coefficient Table

| Variable | Coefficient | Std Error | P-Value | Significant? | Direction & Business Meaning |
|---|---|---|---|---|---|
| **Intercept** | ₹37,032.33 | 48,616.76 | 0.4468 | ❌ | Baseline sales for a Residential store in East with all numerics at 0 |
| `marketing_spend` | 1.160161 | 0.126077 | 0.0000 | ✅ | Each ₹1 in marketing → ₹1.1602 in sales (positive ROI) |
| `footfall` | 28.0682 | 2.4763 | 0.0000 | ✅ | Each additional visitor adds ₹28.07 in sales |
| `avg_discount_pct` | -68,113.21 | 35,997.43 | 0.0594 | ❌ | Higher discounts associated with lower net sales — profitability concern |
| `staff_count` | 3,031.49 | 1,249.89 | 0.0159 | ✅ | Each additional staff member adds ₹3,031 in monthly sales |
| `inventory_availability_pct` | 3,176.72 | 458.27 | 0.0000 | ✅ | Each 1% improvement in inventory availability → ₹3,177 additional sales |
| `customer_rating` | 13,280.97 | 4,767.26 | 0.0057 | ✅ | Each 1-star improvement in rating → ₹13,281 in monthly sales |
| `holiday_flag` | 13,035.53 | 6,588.69 | 0.0488 | ✅ | Holiday months generate ₹13,036 more in sales |
| `store_type_High_Street` vs Residential | 19,551.42 | 5,995.76 | 0.0012 | ✅ | High Street stores outperform Residential stores by ₹19,551 |
| `store_type_Airport` vs Residential | 41,282.91 | 9,363.41 | 0.0000 | ✅ | Airport stores outperform Residential stores by ₹41,283 |
| `store_type_Mall` vs Residential | 29,336.94 | 6,619.61 | 0.0000 | ✅ | Mall stores outperform Residential stores by ₹29,337 |

### Model Performance
| Metric | Value |
|---|---|
| R-Squared | **0.8309** — explains 83.1% of variance |
| Adj. R-Squared | **0.8255** — penalised for 10 predictors |
| F-Statistic | **151.88** (p = 0.000000) — model is overall significant |
| RMSE | **₹43,352** — average prediction error |

---

## Important: Association ≠ Causation

Regression coefficients show **correlation and association**, not causal relationships. For example:
- A positive `holiday_flag` coefficient means holiday months *tend to correlate with* higher sales, but does not prove that holidays *cause* more sales.
- `marketing_spend` may be endogenous — high-performing stores may receive *more* marketing budget, creating reverse causality.
- To establish causation, a controlled experiment (randomised A/B test) is required.
