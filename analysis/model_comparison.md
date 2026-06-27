# Task 6: Model Comparison



---

## Overview

This document compares three regression models developed for predicting `monthly_sales` across 80 retail stores over 4 months (320 observations).

| Model | Type | R-squared | Adj. R-squared | Key Strength |
|-------|------|-----------|----------------|--------------|
| **Simple Model 1** | `monthly_sales ~ footfall` | **0.736** | 0.735 | Highest single-variable explanatory power |
| **Simple Model 2** | `monthly_sales ~ marketing_spend` | 0.167 | 0.165 | Shows positive marketing ROI |
| **Multiple Regression** | Full model with numerical + dummies | **0.859** | **0.851** | Best overall fit and actionable insights |

---

## 1. Simple Model 1: `monthly_sales ~ footfall`

### Variables Used
- **Dependent:** `monthly_sales`
- **Independent:** `footfall` (numerical)

### Key Statistics
- **R-squared:** 0.7363 (73.63%)
- **Coefficient (footfall):** +35.68
- **P-value:** < 0.0001 (highly significant)

### Business Usefulness
**Very High.** Footfall is the single strongest predictor of sales. This model clearly shows that increasing store traffic has a direct, linear, and substantial impact on revenue. Useful for:
- Site selection decisions
- Marketing campaign evaluation (traffic lift)
- Staffing and operational planning

### Limitations
- Ignores all other factors (marketing, inventory, staffing, location, etc.)
- Cannot support "what-if" analysis involving multiple levers
- Over-simplifies reality (R² of 0.74 still leaves 26% unexplained)

---

## 2. Simple Model 2: `monthly_sales ~ marketing_spend`

### Variables Used
- **Dependent:** `monthly_sales`
- **Independent:** `marketing_spend` (numerical)

### Key Statistics
- **R-squared:** 0.1672 (16.72%)
- **Coefficient (marketing_spend):** +2.13
- **P-value:** < 0.0001 (significant)

### Business Usefulness
**Moderate.** This model demonstrates that marketing spend has a **positive return** (roughly 2.13×). It is useful for:
- Justifying marketing budgets
- High-level ROI estimation

However, the low R² shows that marketing alone explains very little of sales variation. Many other factors matter more.

### Limitations
- Very low explanatory power
- Does not account for diminishing returns or interaction effects
- Cannot identify *which* marketing activities work best

---

## 3. Multiple Regression Model (Full Model)

### Variables Used
- **Dependent:** `monthly_sales`
- **Numerical Independents (8):** `marketing_spend`, `footfall`, `avg_discount_pct`, `staff_count`, `inventory_availability_pct`, `competitor_distance_km`, `customer_rating`, `holiday_flag`
- **Dummy Variables (7+):** `region_North/South/West`, `store_type_High Street/Mall/Residential`, `month_name_Jan/Feb/Mar-2025`

### Key Statistics
- **R-squared:** **0.8589** (85.89%)
- **Adj. R-squared:** **0.8509**
- **F-statistic:** 122.56 (p < 0.0001)

### Significant Variables (p < 0.05)
| Variable | Coefficient | Direction | Business Meaning |
|----------|-------------|-----------|------------------|
| **footfall** | +27.53 | Positive | Strongest driver |
| **inventory_availability_pct** | +3,003 | Positive | High-impact operational lever |
| **marketing_spend** | +1.24 | Positive | Positive ROI |
| **staff_count** | +3,372 | Positive | Capacity/operational effect |
| **customer_rating** | +12,243 | Positive | Experience matters |
| **holiday_flag** | +20,434 | Positive | Strong seasonal opportunity |
| `region_South` | +21,245 | Positive | Regional advantage |
| `region_West` | +25,955 | Positive | Regional advantage |
| `store_type_Residential` | -44,518 | Negative | Format underperformance |
| `store_type_High Street` | -24,112 | Negative | Format underperformance |

### Business Usefulness
**Very High — Recommended for Decision Making.**

This model provides:
- **Prioritization:** Clear ranking of what moves the needle most (footfall > inventory > staffing > ratings)
- **What-if analysis:** Estimate impact of changing inventory by 5pp, improving ratings by 0.3 points, etc.
- **Strategic insights:** Regional and format performance gaps are quantified
- **Resource allocation:** Helps decide where to invest (e.g., inventory systems vs. more marketing)

### Limitations
- **Endogeneity:** Some variables (footfall, discounts, staff) are likely jointly determined with sales. Coefficients show association, not pure causation.
- **No interactions:** The model assumes effects are additive. In reality, marketing may work better in high-footfall stores, etc.
- **Cross-sectional limitations:** With only 4 months of data, we cannot strongly identify time-based or lagged effects.
- **Omitted variables:** Factors like assortment quality, online competition, local demographics, and promotion calendars are not captured.
- **Some counter-intuitive results:** `competitor_distance_km` being negative likely reflects location quality rather than a direct effect.

---

## Overall Comparison Summary

| Criteria                    | Simple Model 1 (footfall) | Simple Model 2 (marketing) | **Multiple Regression** |
|----------------------------|---------------------------|----------------------------|-------------------------|
| **Explanatory Power (R²)** | High (0.74)              | Low (0.17)                | **Excellent (0.86)**   |
| **Actionable Insights**    | Limited but clear        | Weak                      | **Rich & prioritized** |
| **Handles Multiple Factors**| No                       | No                        | **Yes**                |
| **Supports Decision Making**| Moderate                 | Low                       | **High**               |
| **Risk of Misinterpretation** | Low                    | Moderate                  | Moderate (endogeneity) |
| **Best Used For**          | Quick traffic analysis   | Marketing budget justification | **Strategic planning & resource allocation** |

---

## Recommendation

**Use the Multiple Regression Model** as the primary tool for business decision-making. It provides the best balance of explanatory power, statistical rigor, and actionable insights.

The simple models are useful for quick directional understanding and communication but should not be used in isolation for major decisions.

**Next Steps Suggested:**
- Add interaction terms (e.g., marketing × footfall)
- Explore panel data fixed effects models
- Collect more granular data (daily/weekly) for better causality
- Run scenario simulations based on the multiple regression coefficients
