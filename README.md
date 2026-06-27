# Retail Store Performance Regression Analysis

**Business Context:**  
A retail chain leadership team wants to understand the key drivers of monthly sales performance across stores. They are considering business actions such as increasing marketing spend, improving inventory availability, changing discounting strategy, reallocating staff, and prioritizing certain store types or regions.

This project applies regression analysis to identify the most important factors associated with monthly sales and provides actionable recommendations for leadership.

---

## Business Problem Summary

The leadership team needs data-driven insights to answer:
- What factors most strongly influence monthly sales across stores?
- Where should the organization focus resources to improve performance?
- Are there meaningful differences by region or store format?
- What are the risks of misinterpreting the data?

This analysis addresses these questions using multiple linear regression on store performance data.

---

## Dataset Description

**Source:** `business_regression_data.xlsx` (store_performance sheet)  
**Observations:** 320 store-month records (80 stores × 4 months)  
**Time Period:** January 2025 – April 2025

### Variables Overview

| Category              | Variables |
|-----------------------|-----------|
| **Identifiers**       | `store_id`, `month` |
| **Location & Format** | `region` (East, North, South, West), `store_type` (Airport, High Street, Mall, Residential) |
| **Marketing**         | `marketing_spend`, `avg_discount_pct` |
| **Operations**        | `footfall`, `staff_count`, `inventory_availability_pct`, `competitor_distance_km` |
| **Customer**          | `customer_rating`, `holiday_flag` |
| **Outcome**           | `monthly_sales` (primary), `monthly_profit` (secondary) |

**Note on Currency:** The original dataset does not explicitly specify the currency unit for monetary variables (`marketing_spend`, `monthly_sales`, `monthly_profit`). All monetary values in this analysis are presented without assuming a specific currency.

---

## Dependent and Independent Variables

**Dependent Variable:** `monthly_sales`

**Independent Variables Considered:**
- Numerical: `marketing_spend`, `footfall`, `avg_discount_pct`, `staff_count`, `inventory_availability_pct`, `competitor_distance_km`, `customer_rating`, `holiday_flag`
- Categorical: `region`, `store_type`, `month_name` (engineered from `month`)

---

## Regression Approach

### Methodology
- **Primary Model:** Multiple Linear Regression using Ordinary Least Squares (OLS)
- **Robust Standard Errors:** HC3 (heteroskedasticity-consistent) to account for non-constant variance
- **Missing Value Treatment:** Median imputation for `competitor_distance_km` and `customer_rating`
- **Categorical Encoding:** One-hot encoding (dummy variables) with reference category dropped

### Why Multiple Regression?
Simple regression models (single predictor) provide directional insights but cannot account for the combined effect of multiple factors. Multiple regression allows us to:
- Estimate the unique contribution of each variable while holding others constant
- Rank variables by importance
- Quantify regional and format differences
- Support "what-if" scenario analysis

---

## Dummy Variable Approach

Categorical variables (`region`, `store_type`, `month_name`) were converted to dummy variables using one-hot encoding.

**Reference Categories Selected:**
| Variable     | Reference Category | Rationale |
|--------------|--------------------|-----------|
| `region`     | **East**           | Serves as baseline geography |
| `store_type` | **Airport**        | Highest-performing format in initial analysis |
| `month_name` | **Apr-2025**       | Last period; convenient baseline for trend interpretation |

**Why Drop One Category?**  
Including all categories creates perfect multicollinearity (the "dummy variable trap"), making coefficient estimation impossible. Dropping one category allows interpretation of other categories *relative to* the reference.

---

## Model Comparison Summary

| Criteria                    | Simple Model 1 (footfall) | Simple Model 2 (marketing) | **Multiple Regression** |
|----------------------------|---------------------------|----------------------------|-------------------------|
| **R-squared**              | 0.736                     | 0.167                      | **0.859**               |
| **Adj. R-squared**         | 0.735                     | 0.165                      | **0.851**               |
| **Significant Predictors** | 1                         | 1                          | **9+**                  |
| **Explanatory Power**      | High                      | Low                        | **Excellent**           |
| **Business Actionability** | Moderate                  | Low-Moderate               | **High**                |
| **Best Use Case**          | Quick communication       | Marketing budget justification | **Strategic planning & decisions** |

**Conclusion:** The Multiple Regression model provides the best balance of explanatory power, statistical rigor, and actionable insights. Simple models are useful for quick communication but insufficient for major decisions.

---

## Final Model Selected

**Selected Model:** Multiple Linear Regression with HC3 robust standard errors  
**R-squared:** 0.859  
**Adj. R-squared:** 0.851  
**Observations:** 320

**Key Variables in Final Model:**
- Numerical: `footfall`, `inventory_availability_pct`, `staff_count`, `customer_rating`, `marketing_spend`, `holiday_flag`, `avg_discount_pct`, `competitor_distance_km`
- Dummy Variables: `region_North/South/West`, `store_type_High Street/Mall/Residential`, `month_name_Jan/Feb/Mar-2025`

---

## Business Recommendation

### Top Priorities for Leadership

| Priority | Focus Area                    | Rationale | Recommended Action |
|----------|-------------------------------|-----------|--------------------|
| **1**    | **Footfall Generation**       | Strongest driver (+27.53 per visitor) | Invest in local marketing, partnerships, and visibility initiatives |
| **2**    | **Inventory Availability**    | High impact (+3,003 per 1pp)         | Improve supply chain reliability and reduce stockouts |
| **3**    | **Staffing & Execution**      | Strong operational lever (+3,372 per staff) | Review staffing models, especially in underperforming formats |
| **4**    | **Customer Experience**       | High value (+12,243 per rating point) | Focus on service quality and store environment |
| **5**    | **Regional & Format Gaps**    | Material performance differences     | Investigate why East region and Residential/High Street formats underperform |

### Variables to Treat with Caution

- `avg_discount_pct`: Not statistically significant; negative direction may reflect reverse causality.
- `competitor_distance_km`: Significant but likely a proxy for location quality rather than a direct causal effect.

### Key Business Actions

1. **Short-term (30–60 days):** Audit inventory processes and identify low-availability stores. Conduct footfall diagnostic comparing top vs. bottom performers.
2. **Medium-term (60–180 days):** Launch regional performance turnaround program for East region. Develop customer experience improvement initiative. Review Residential and High Street format strategy.

---

## Assumptions and Limitations

### Assumptions
- Linear relationships between predictors and sales (reasonable approximation based on model fit).
- No perfect multicollinearity after dropping reference categories.
- Missing values are missing at random (imputed with median).

### Limitations

| Limitation | Description | Implication |
|------------|-------------|-------------|
| **Association ≠ Causation** | Regression shows statistical relationships, not proven cause-and-effect. | Major interventions should be tested via pilots or A/B testing before full rollout. |
| **Endogeneity** | Some variables (footfall, staff, discounts) are likely jointly determined with sales. | Coefficients may be biased; results show association, not pure causal impact. |
| **Omitted Variables** | Local promotions, competitor actions, assortment quality, demographics, and execution quality not captured. | Large residuals in some stores indicate important missing factors. |
| **Limited Time Window** | Only 4 months of data. | Results reflect average relationships during this period; may not generalize to other time periods or economic conditions. |
| **Cross-Sectional Design** | Limited ability to identify lagged or time-based effects. | Dynamic effects (e.g., marketing carryover) cannot be fully captured. |

---

## Screenshots Included

The following visual evidence is provided in the deliverables:

| Screenshot | File | Purpose |
|------------|------|---------|
| Simple Regression Output | `simple_regression_output.png` | Detailed regression table for footfall model |
| Multiple Regression Output | `multiple_regression_output.png` | Full model coefficients, significance, and fit statistics |
| Residual Analysis | `residuals_preview.png` | Residual distribution, actual vs predicted, and top outliers |
| Model Comparison | `model_comparison_preview.png` | Side-by-side comparison of simple vs multiple models |

---

## Deliverables

| File | Description |
|------|-------------|
| `README.md` | Project overview and documentation (this file) |
| `model_equations.md` | Simple and multiple regression equations with business interpretation |
| `simple_regression_results.md` | Documentation of two simple regression models |
| `multiple_regression_results.md` | Full multiple regression model results and interpretation |
| `residual_analysis.md` | Analysis of model residuals and outlier stores |
| `model_comparison.md` | Detailed comparison of simple vs multiple models |
| `final_recommendation.md` | Executive summary and actionable business recommendations |
| `regression_summary.xlsx` | Excel workbook with model comparison and insights |
| `regression_workbook.xlsx` | Complete workbook with data, models, and outputs |

---

**Project completed following best practices for transparency, statistical rigor, and business relevance.**  
*All monetary values presented without assuming a specific currency, as none was specified in the original dataset.*