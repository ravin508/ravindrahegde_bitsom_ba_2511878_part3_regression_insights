# Final Business Recommendation

**Project:** Retail Store Performance Regression Analysis  
**Date:** June 2026

---

## Executive Summary

Based on a comprehensive multiple regression analysis of 320 store-month observations across 80 retail stores, we have identified the key drivers of monthly sales performance. This analysis provides leadership with data-driven priorities for improving store performance.

**Key Finding:**  
**Footfall, inventory availability, and operational execution** are the strongest levers for increasing monthly sales. Marketing delivers positive returns but is secondary to core operational factors. Significant performance gaps exist between regions and store formats.

---

## 1. Which Factors Appear Most Strongly Associated with Monthly Sales?

From the multiple regression model (R² = 0.859), the following variables show the strongest statistical association with monthly sales:

### Tier 1: High-Impact Drivers (Strongest Association)

| Rank | Variable                        | Coefficient | Business Impact |
|------|---------------------------------|-------------|-----------------|
| 1    | **Footfall**                    | +27.53     | Every additional visitor brings ~27.53 monetary units in sales. **Strongest single driver.** |
| 2    | **Inventory Availability %**    | +3,003     | A 1 percentage point improvement in product availability is worth ~3,003 monetary units per store per month. |
| 3    | **Staff Count**                 | +3,372     | Each additional staff member is associated with ~3,372 monetary units in extra sales. |
| 4    | **Customer Rating**             | +12,243    | Improving average rating by 1 point is worth over 12,243 monetary units per month per store. |

### Tier 2: Moderate-Impact Drivers

| Variable              | Coefficient | Business Impact |
|-----------------------|-------------|-----------------|
| **Holiday Flag**      | +20,434    | Meaningful holiday months deliver a clear sales lift. |
| **Marketing Spend**   | +1.24      | Positive ROI (~1.24×), but lower impact than operational factors. |
| **Region (West/South)** | +21,245 to +25,955 | West and South regions significantly outperform East. |
| **Store Format**      | -24,112 to -44,518 | Residential and High Street formats significantly underperform Airport format. |

---

## 2. Which Variables Should Leadership Focus On?

Based on statistical significance, effect size, and actionability, we recommend leadership prioritize the following:

### Primary Focus Areas (High ROI Potential)

| Priority | Area                        | Recommended Actions |
|----------|-----------------------------|---------------------|
| **1**    | **Footfall Generation**     | Invest in local marketing, partnerships, events, and location-based strategies to drive store traffic. |
| **2**    | **Inventory Availability**  | Improve supply chain reliability, reduce stockouts, and optimize replenishment processes. Quick wins likely. |
| **3**    | **Staffing & Execution**    | Review staffing models, especially in underperforming formats. Ensure adequate coverage during peak periods. |
| **4**    | **Customer Experience**     | Focus on service quality, staff training, and store environment to improve customer ratings. |
| **5**    | **Regional Performance**    | Investigate why East region underperforms West and South. Address gaps in execution or assortment. |

### Secondary Focus

- **Marketing Spend**: Continue investment but treat it as a supporting lever rather than the primary driver. Focus on campaigns that also drive footfall.
- **Holiday Planning**: Plan inventory, staffing, and promotions aggressively around holiday periods.

---

## 3. Which Variables Should Not Be Over-Interpreted?

Some variables show statistical significance but should be interpreted with caution:

| Variable                    | Finding                          | Caution |
|----------------------------|----------------------------------|--------|
| **`avg_discount_pct`**     | Not statistically significant (p=0.195). Negative direction. | May reflect reverse causality (stores discount more when sales are weak). Do not assume "discounting hurts sales" without further analysis. |
| **`competitor_distance_km`** | Statistically significant but negative coefficient. | Likely a **proxy for location quality** rather than a direct causal effect. Stores farther from competitors may be in weaker locations. |
| **Most `month_name` dummies** | Mostly insignificant            | Time-based effects are relatively stable after controlling for other factors. |

**Recommendation:** Avoid making major strategic decisions (e.g., "we should discount less") based solely on these variables without additional investigation.

---

## 4. What Business Actions Would You Recommend?

### Immediate Actions (Next 30–60 Days)

1. **Audit Inventory Processes**
   - Identify stores with lowest inventory availability.
   - Implement targeted interventions to reduce stockouts.

2. **Footfall Diagnostic**
   - Compare top-performing vs. bottom-performing stores on footfall drivers (local marketing, visibility, promotions).
   - Develop a playbook based on best practices from high-footfall stores.

3. **Format Strategy Review**
   - Conduct deep-dive analysis on Residential and High Street formats.
   - Identify whether underperformance is due to location, assortment, execution, or customer demographics.

### Medium-Term Actions (60–180 Days)

4. **Regional Performance Turnaround (East Region)**
   - Compare operational practices between East and West/South regions.
   - Identify gaps in execution, assortment, or local marketing.

5. **Customer Experience Program**
   - Roll out targeted training and store environment improvements.
   - Track impact on customer ratings and sales.

6. **Marketing Optimization**
   - Shift marketing mix toward activities that also drive footfall.
   - Measure footfall lift alongside sales ROI.

---

## 5. What Risks or Limitations Should Leadership Keep in Mind?

### Key Limitations of This Analysis

| Limitation | Description | Implication |
|------------|-------------|-------------|
| **Association ≠ Causation** | Regression shows relationships, not proven cause-and-effect. | Interventions based on this model should be tested (A/B testing or pilot programs) before full rollout. |
| **Endogeneity** | Some variables (footfall, staff count, discounts) are likely jointly determined with sales. | Coefficients may be biased. Results show association, not pure causal impact. |
| **Omitted Variables** | Factors like local promotions, competitor actions, assortment quality, online competition, and demographics are not captured. | Large residuals (±100,000+ monetary units) in some stores indicate important missing factors. |
| **Cross-Sectional Nature** | Only 4 months of data. Limited ability to identify time-based or lagged effects. | Results reflect average relationships over this period; may not hold in different economic or competitive conditions. |
| **Format & Regional Gaps** | We observe performance differences but do not fully explain *why* they exist. | Further qualitative investigation is needed before making major format or regional strategy changes. |

### Risks of Misinterpretation

- Over-investing in marketing while under-investing in inventory and operations.
- Making aggressive discounting changes based on weak evidence.
- Assuming Residential/High Street formats are inherently inferior without understanding root causes.

---

## 6. Why Does Regression Show Association but Not Automatically Prove Causation?

Regression analysis identifies **statistical associations** — variables that move together. However, it does not automatically prove that changing one variable *causes* a change in another for several reasons:

| Reason | Explanation | Example from This Study |
|--------|-------------|-------------------------|
| **Reverse Causality** | Sales performance may influence the predictor, not the other way around. | Stores with weak sales may discount more → negative relationship between discounts and sales. |
| **Omitted Variable Bias** | An unobserved factor affects both the predictor and sales. | Better store managers may drive both higher footfall *and* higher sales. |
| **Simultaneity** | Predictor and outcome are jointly determined. | Footfall and sales influence each other in real time. |
| **Selection Effects** | Stores in certain locations or formats may differ systematically in unmeasured ways. | Residential stores may be located in areas with different customer demographics or competition levels. |

**Implication for Leadership:**  
Regression provides excellent **directional guidance** and **prioritization**, but major decisions (especially those involving significant investment or strategic change) should be validated through controlled experiments, pilot programs, or additional qualitative research.

---

## Conclusion

The regression analysis provides a clear, evidence-based roadmap for improving store performance:

- **Focus first on footfall, inventory, and execution** — these are the highest-impact, most actionable levers.
- **Treat marketing as a supporting investment**, not the primary driver.
- **Investigate regional and format gaps** — the performance differences are real and material.
- **Test before scaling** — use the model for prioritization, but validate causality through pilots and experiments.

This analysis gives leadership a strong foundation for data-driven decision-making while highlighting the importance of combining quantitative insights with operational understanding and controlled testing.

---

**End of Final Recommendation**