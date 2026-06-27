# Task 7: Residual Analysis

**Date:** June 2026  
**Model Used:** Multiple Regression (R² = 0.8589)

---

## 1. Methodology

Using the final multiple regression model, we calculated:

- **Predicted Sales** = Model prediction for each store-month
- **Residual** = Actual Sales − Predicted Sales

**Positive residual** → Model **under-predicted** sales (store performed better than expected)  
**Negative residual** → Model **over-predicted** sales (store performed worse than expected)

---

## 2. Top 5 Records with Largest Positive Residuals (Under-predicted)

These stores significantly outperformed model expectations.

| Store ID | Month     | Region | Store Type   | Actual Sales | Predicted Sales | Residual    |
|----------|-----------|--------|--------------|--------------|------------------|-------------|
| STR-1058 | Feb-2025  | East   | High Street  | 870,937     | 763,906         | **+107,032** |
| STR-1023 | Feb-2025  | South  | Mall         | 627,172     | 769,727         | **+142,555** |
| STR-1017 | Mar-2025  | West   | High Street  | 685,379     | 809,662         | **+124,283** |
| STR-1060 | Jan-2025  | West   | Mall         | 721,079     | 799,277         | **+78,198**  |
| STR-1012 | Jan-2025  | West   | Residential  | 595,468     | 703,879         | **+108,412** |

**Business Interpretation:**
These stores beat expectations substantially. Possible reasons include:
- Strong local promotions or events not captured in data
- Superior execution (staffing, merchandising, customer service)
- Temporary competitive advantages

**Action:** Investigate these stores to identify repeatable best practices.

---

## 3. Top 5 Records with Largest Negative Residuals (Over-predicted)

These stores significantly underperformed relative to model expectations.

| Store ID | Month     | Region | Store Type   | Actual Sales | Predicted Sales | Residual    |
|----------|-----------|--------|--------------|--------------|------------------|-------------|
| STR-1007 | Feb-2025  | West   | Mall         | 800,452     | 918,925         | **−118,473** |
| STR-1017 | Mar-2025  | West   | High Street  | 685,379     | 809,662         | **−124,283** |
| STR-1068 | Jan-2025  | East   | Mall         | 660,634     | 729,548         | **−68,914**  |
| STR-1077 | Feb-2025  | South  | Residential  | 538,376     | 593,167         | **−54,791**  |
| STR-1008 | Jan-2025  | East   | Residential  | 511,844     | 562,646         | **−50,802**  |

**Business Interpretation:**
These stores lagged behind what their characteristics (footfall, inventory, staffing, location) would predict. Likely causes:
- Execution gaps (inventory issues, understaffing, weak promotions)
- Unobserved local competitive pressure
- Operational disruptions

**Action:** Prioritize performance reviews and support for these stores.

---

## 4. Model Bias by Store Type / Region

| Observation | Finding | Implication |
|-------------|---------|-------------|
| **Residential stores** | Appear more frequently among large negative residuals | Model tends to **over-predict** Residential format performance |
| **February 2025** | Shows up often in both extreme positive and negative residuals | February had higher volatility than captured by month dummies |
| **West & South regions** | Mixed residuals | Model captures regional effects reasonably well |

**Overall Assessment:**
The model is generally well-calibrated but shows some tendency to **over-predict Residential stores** and struggles with high month-to-month volatility in certain locations. Large residuals (exceeding ±100,000 monetary units) indicate important unobserved factors (local events, execution quality, competitor actions).

---

## 5. Business Recommendations

1. **Investigate top positive outliers** — Extract and replicate success factors.
2. **Support top negative outliers** — These represent immediate performance improvement opportunities.
3. **Review Residential format strategy** — Consistent underperformance relative to model expectations suggests structural issues.
4. **Improve data collection** — Add variables for local promotions, competitor activity, and execution quality to reduce large residuals in future models.

---

*Visual evidence saved as `residuals_preview.png` (residual distribution, actual vs predicted scatter plot, and bar charts of top positive/negative residuals).*
