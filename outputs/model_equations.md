# Model Equations Documentation

**Project:** Retail Store Performance Regression Analysis  
**Date:** June 2026

---

## 1. Overview

This document presents the regression equations developed to understand what drives monthly sales across 80 retail stores over four months. We built both simple models (useful for quick communication) and a comprehensive multiple regression model (recommended for strategic decision-making).

**Note:** The original dataset does not explicitly specify the currency unit for monetary values (marketing_spend, monthly_sales, monthly_profit). All figures in this document are presented without assuming a specific currency.

---

## 2. Simple Regression Equations

### Model 1: Impact of Customer Footfall on Sales

**Regression Equation:**
```
Monthly Sales = 446411 + 35.68 × Footfall
```

**Business Explanation of Coefficients:**

- **Intercept (446411):** This represents the theoretical baseline sales when no customers visit the store. While not realistic in practice, it serves as the starting point of the relationship.
- **Footfall Coefficient (35.68):** For every additional customer who enters the store in a month, monthly sales are expected to increase by approximately **35.68** monetary units.

**Business Meaning:**  
Footfall is the single most powerful driver of sales. If a store increases its monthly footfall by 1,000 visitors, it can expect roughly **35,680** monetary units in additional revenue, assuming other factors remain constant.

---

### Model 2: Impact of Marketing Spend on Sales

**Regression Equation:**
```
Monthly Sales = 560777 + 2.13 × Marketing Spend
```

**Business Explanation of Coefficients:**

- **Intercept (560777):** Expected sales level with zero marketing investment.
- **Marketing Spend Coefficient (2.13):** Every additional unit spent on marketing is associated with **2.13** units in additional sales.

**Business Meaning:**  
Marketing delivers a positive return. Spending 100,000 units on marketing is associated with approximately **213,000** units in extra sales. However, this model explains only a modest portion of total sales variation, meaning many other factors also influence performance.

---

## 3. Multiple Regression Equation (Recommended Final Model)

This is our **primary model** for business planning and decision-making.

**Simplified Business Equation:**

```
Monthly Sales = 
    95327 (Baseline)
  + 1.24 × Marketing Spend
  + 27.53 × Footfall
  + 3003 × Inventory Availability %
  + 3372 × Number of Staff
  + 12243 × Average Customer Rating
  + 20434 × Holiday Month Premium
  + Adjustments for Region (relative to East)
  + Adjustments for Store Format (relative to Airport)
```

**Statistical Form:**

```
monthly_sales = β₀ 
              + β₁·marketing_spend 
              + β₂·footfall 
              + β₃·inventory_availability_pct 
              + β₄·staff_count 
              + β₅·customer_rating 
              + β₆·holiday_flag 
              + β₇·region_North + β₈·region_South + β₉·region_West 
              + β₁₀·store_type_HighStreet + β₁₁·store_type_Mall + β₁₂·store_type_Residential 
              + month dummies 
              + ε
```

**Model Performance:**
- **R-squared:** 0.859 (explains 85.9% of variation in monthly sales)
- **Adjusted R-squared:** 0.851

---

## 4. Business Interpretation of Key Coefficients

| Variable                        | Coefficient     | Business Interpretation |
|---------------------------------|-----------------|-------------------------|
| **Footfall**                    | **+27.53**     | The strongest driver. Every extra visitor is worth about **27.53** monetary units in sales. |
| **Inventory Availability %**    | **+3003**      | Improving product availability by just 1 percentage point adds roughly **3000** monetary units in monthly sales per store. Highly actionable. |
| **Marketing Spend**             | **+1.24**      | Positive return. Every unit spent on marketing brings back about **1.24** units in sales. |
| **Staff Count**                 | **+3372**      | Adding one more team member is associated with **3372** monetary units in extra sales (reflects service capacity and operational strength). |
| **Customer Rating**             | **+12243**     | Improving average customer rating by 1 full point is worth over **12243** monetary units per month per store. |
| **Holiday Flag**                | **+20434**     | Months with meaningful holidays deliver an average **20434** monetary units sales lift. Plan accordingly. |

---

## 5. Dummy Variables and Reference Categories

Categorical variables (region and store type) were converted into dummy variables. To avoid statistical problems, we dropped one category from each variable. This dropped category serves as the **reference point** against which other categories are compared.

### Region Dummies (Reference Category: **East**)

| Dummy Variable     | Coefficient | Business Meaning |
|--------------------|-------------|------------------|
| `region_South`     | +21245     | South region stores generate **21245** monetary units more sales per month than comparable East region stores. |
| `region_West`      | +25955     | West region stores generate **25955** monetary units more sales per month than East region stores. |
| `region_North`     | +10254     | North region stores perform better than East, but the difference is not statistically strong. |

**Business Insight:** The East region is underperforming relative to West and South. This gap deserves investigation.

### Store Type Dummies (Reference Category: **Airport**)

| Dummy Variable              | Coefficient   | Business Meaning |
|----------------------------|---------------|------------------|
| `store_type_Residential`   | **−44518**   | Residential stores generate **44518** monetary units less per month than Airport stores (all else equal). |
| `store_type_High Street`   | **−24112**   | High Street stores generate **24112** monetary units less than Airport stores. |
| `store_type_Mall`          | −11665       | Mall stores perform slightly below Airport stores (difference not statistically significant). |

**Business Insight:** The Airport format significantly outperforms Residential and High Street formats. This performance gap should be reviewed strategically.

---

## 6. Final Model Selected and Rationale

**Selected Model:** Multiple Regression Model (including numerical variables + dummy variables for region and store type)

**Why this model was chosen:**

| Reason | Business Explanation |
|--------|----------------------|
| **Highest Explanatory Power** | Explains nearly 86% of sales variation — much stronger than any single-variable model. |
| **Clear Prioritization** | Shows leadership exactly which levers move the needle most (footfall > inventory > staffing > customer experience). |
| **Supports Scenario Planning** | Enables "what-if" analysis (e.g., "What happens if we improve inventory by 5 points and ratings by 0.3 points?"). |
| **Reveals Strategic Gaps** | Quantifies important differences between regions (West/South vs East) and store formats (Airport vs Residential). |
| **Statistically Reliable** | Strong overall model significance and uses robust methods to handle data characteristics. |

While simple models are helpful for quick explanations, the multiple regression model provides the richest and most reliable foundation for strategic decisions.

---

## Summary

The final model tells a clear business story:

> **Footfall remains the biggest driver of sales**, but **inventory availability, staffing levels, and customer experience** are also powerful and actionable levers. Marketing delivers a positive return but is not the dominant factor. There are meaningful and consistent performance differences between regions and store formats that leadership should address.

This model gives the organization a data-driven basis for prioritizing investments and operational improvements across the chain.

---

**End of Model Equations Documentation**