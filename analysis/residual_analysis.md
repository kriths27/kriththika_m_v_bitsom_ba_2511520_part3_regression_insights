# Residual Analysis — Multiple Regression Model
**Model:** MLR — monthly_sales ~ 10 predictors

A **residual** = Actual Sales − Model Predicted Sales.  
- **Positive residual**: Model UNDERESTIMATED sales → store performed BETTER than predicted  
- **Negative residual**: Model OVERESTIMATED sales → store performed WORSE than predicted

---

## Top 5 Positive Residuals (Model Underestimated)

| Rank | Store ID | Month | Region | Store Type | Actual Sales | Predicted | Residual |
|---|---|---|---|---|---|---|---|
| 1 | STR-1030 | 2025-02 | West | Residential | ₹820,519 | ₹717,203 | **+₹103,317** |
| 2 | STR-1028 | 2025-04 | East | Mall | ₹713,611 | ₹611,902 | **+₹101,709** |
| 3 | STR-1069 | 2025-04 | West | High Street | ₹686,738 | ₹590,520 | **+₹96,217** |
| 4 | STR-1027 | 2025-03 | West | High Street | ₹795,154 | ₹699,583 | **+₹95,571** |
| 5 | STR-1075 | 2025-02 | West | High Street | ₹763,162 | ₹671,555 | **+₹91,608** |

### Business Interpretation of Positive Residuals
These stores outperformed the model's prediction. Possible reasons:
1. **Local market events** not captured in the dataset (festivals, local promotions, nearby competitor closure)
2. **Staff quality or management effectiveness** — high-performing teams can punch above the model's ceiling
3. **Micro-location advantages** — a store with unusually high footfall conversion (not just footfall volume)
4. **Underreported promotional activity** — in-store promotions that don't appear in `marketing_spend`
5. **Brand loyalty effects** — established customer bases in specific localities

**Recommended Action:** Investigate these stores for replicable best practices. Interview store managers to identify what they're doing differently.

---

## Top 5 Negative Residuals (Model Overestimated)

| Rank | Store ID | Month | Region | Store Type | Actual Sales | Predicted | Residual |
|---|---|---|---|---|---|---|---|
| 1 | STR-1017 | 2025-03 | West | High Street | ₹685,379 | ₹842,591 | **₹-157,212** |
| 2 | STR-1023 | 2025-02 | South | Mall | ₹627,172 | ₹753,779 | **₹-126,607** |
| 3 | STR-1012 | 2025-01 | West | Residential | ₹595,468 | ₹712,673 | **₹-117,205** |
| 4 | STR-1007 | 2025-02 | West | Mall | ₹800,452 | ₹899,750 | **₹-99,298** |
| 5 | STR-1009 | 2025-01 | North | Residential | ₹641,865 | ₹736,287 | **₹-94,422** |

### Business Interpretation of Negative Residuals
These stores underperformed relative to what the model expected given their inputs. Possible reasons:
1. **Operational issues** — staffing disruptions, stock-outs, or infrastructure problems not in the data
2. **External shocks** — road closures, local incidents, or weather events affecting specific locations
3. **Data quality issues** — incorrect footfall or marketing spend records for these stores/months
4. **High competition not captured** — nearby competitors whose proximity or promotions aren't in the dataset
5. **Consumer sentiment issues** — recent negative reviews or incidents affecting local brand perception

**Recommended Action:** Flag these stores for operational review. Cross-reference with store manager logs and local news.

---

## Overall Residual Distribution

| Metric | Value |
|---|---|
| Mean Residual | ₹0.00 (expected ≈ 0) |
| Std Dev of Residuals | ₹42,667.13 |
| Max Positive Residual | +₹103,316.54 |
| Max Negative Residual | ₹-157,211.95 |
| % Residuals within ±1 RMSE | 69.1% |

A near-zero mean residual ✅ confirms the model is not systematically biased. The spread indicates individual store-level variation the model cannot fully explain — which is expected and appropriate.
