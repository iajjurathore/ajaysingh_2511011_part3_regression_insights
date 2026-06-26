### Name - Ajay Singh
### Id - Bitsom_Ba_2511011


##  1. Business Problem Summary
You are working as a business analyst for a retail chain.

The leadership team wants to understand what factors are driving monthly sales performance across stores. They are considering business actions such as increasing marketing spend, improving inventory availability, changing discounting strategy, reallocating staff, and prioritizing certain store types or regions.

Your task is to use regression analysis to identify which factors appear most strongly associated with monthly sales and provide a business recommendation.

##  2. Dataset Description
The analysis was performed utilizing the master data asset business_regression_data.xlsm (specifically the store_performance worksheet).
 * **Data Scale:** The matrix encompasses **320 complete store observations** across **14 structural columns**.
 * **Granular Attributes:** The dataset monitors unique store identifiers (store_id), fiscal periods (month), regional assignments (region), physical setups (store_type), operational variables (marketing_spend, footfall, avg_discount_pct, staff_count, inventory_availability_pct, competitor_distance_km, holiday_flag, customer_rating), and high-level outputs (monthly_sales, monthly_profit).

##  3. Dependent and Independent Variables
To isolate revenue drivers accurately, specific metrics were categorized or explicitly excluded to prevent multicollinearity and target leakage:
 * **Dependent Variable (Y Target):** monthly_sales.
 * **Numerical Independent Variables (X):** footfall, marketing_spend, avg_discount_pct, staff_count, inventory_availability_pct, competitor_distance_km, and customer_rating.
 * **Categorical Independent Variables (X):** region and store_type.
 * **Excluded Variables:** store_id and month (non-predictive identifiers), alongside monthly_profit (excluded to protect against clear mathematical endogeneity and circular logic).

##  4. Regression Approach
The analysis adopted a phased statistical approach to isolate individual variable behaviors before deploying a multi-variable ecosystem:
 * **Phase 1: Simple Linear Regression (Baseline Testing):** Tested individual core inputs against revenue to benchmark raw predictive strength.
 * **Phase 2: Multiple Linear Regression (Holistic Modeling):** Evaluated all statistically viable independent variables simultaneously to control for confounding effects and observe how factors interact under real-world retail conditions.

##  5. Dummy Variable Approach
The categorical variable store_type was converted into quantitative indicators to observe structural real estate yields.
 * **Dummies Created:** Residential_dummy, HighStreet_dummy, and Mall_dummy.
 * **Reference Benchmark Category:** **Airport Stores** was utilized as the omitted baseline category. All dummy variable impacts are measured directly as a premium or deficit against the average revenue benchmark of an Airport location.
##  6. Model Comparison Summary
The iterative modeling process demonstrated a dramatic increase in predictive accuracy:
 * **Model 1(Marketing Simple Regression):** Demonstrated weak standalone capabilities, explaining only 16.72\% of variance (R^2 = 0.1672; p = 2.48 \times 10^{-14}).
 * **Model 2 (Footfall Simple Regression):** Proved a strong single-variable relationship, explaining 73.63\% of revenue variance (R^2 = 0.7363; p = 4.75 \times 10^{-94}).
 * **Model 3 (Multiple Linear Regression):** Significantly reduced the portfolio Standard Error down to 44,456.41, successfully explaining **81.99\% of total cross-store variance** (\text{Adjusted } R^2 = 0.8165).

##  7. Final Model Selected
The **Multiple Linear Regression Model (Model 3)** was selected as the definitive corporate tool due to its high predictive confidence and contextual coverage.

### Variable Significance Metrics:
 * **footfall:** Highly Significant (p = 1.23 \times 10^{-102})
 * **marketing_spend:** Highly Significant (p = 7.59 \times 10^{-18})
 * **inventory_availability_pct:** Highly Significant (p = 2.09 \times 10^{-10})
 * **Residential_dummy:** Highly Significant Deficit (p = 3.99 \times 10^{-5})
 * **HighStreet_dummy:** Significant Deficit (p = 0.0152)
 * **Mall_dummy:** **Statistically Non-Significant** (p = 0.251)

##  8. Business Recommendation
 * **Protect the Conversion Funnel:** Since each customer entry yields **$33.68** in revenue, prioritize operational programs that maximize capture rate and footfall.
 * **Mitigate Inventory Stockouts:** Every single percentage point drop in inventory availability costs the store an average of **$3,062.93** per month. Leadership should mandate robust safety-stock parameters on core SKUs.
 * **Optimize Store Placements:** Favor high-yielding Airport expansions. Completely halt new standalone Residential formats due to their steep structural revenue deficit of **-$39,654.57** relative to travel hubs.
 * **Investigate Portfolio Outliers:** Dispatch operational auditors to resolve revenue leakages at severe underperforming nodes **STR-1017** and **STR-1023** (large negative residuals), while scaling best practices from hyper-performing units **STR-1073** and **STR-1030** (large positive residuals).

##  9. Assumptions and Limitations
 * **Omitted Variables:** The data architecture does not account for seasonality, shifts in macroeconomic consumer sentiment, or localized competitor pricing matches.
 * **Association vs. Causation Guardrail:** The model indicates mathematical association, not direct causation. For instance, while marketing intensity correlates with higher revenue, high-performing locations may simply be granted larger budgets by default. Strategy must treat these outputs as indicators rather than absolute causal links.
 * **The Mall Variable Interpretation:** Leadership must not mistake the negative coefficient of the Mall dummy as an indicator of poor performance; its high p-value (0.251) proves mall locations perform on par with airports once traffic and inventory metrics are equalized.

## 📸 10. Screenshots Included
All relevant statistical diagnostics, workbook iterations, and model comparisons have been visually cataloged. This verification framework features full verification captures from the project sheets:
 1. Simple_Regression
 2. Multiple_Regression 
 3. residuals_preview
 4. Model Comparison 