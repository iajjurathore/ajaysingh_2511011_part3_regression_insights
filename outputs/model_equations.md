# Task 8: Write Model Equations

---

## 1. Simple Regression Equations



### Model 1 — Monthly Sales vs Marketing Spend

```
monthly_sales = 560,777.35 + 2.13 × marketing_spend
```

**R² = 0.1672** | **P-value = 2.48E-14**  Significant

**Coefficient Explanation:**
- **560,777.35 (Intercept):** Predicted monthly sales when marketing spend is zero.
- **2.13 (marketing_spend):** For every £1 extra spent on marketing, monthly sales increase by only £2.13. This is statistically significant but the return on investment is very low.

**Business Meaning:** Marketing spend alone is a weak predictor — it only explains 16.7% of sales variation. While spending on marketing does help, other factors matter much more.

### Model 2 — Monthly Sales vs Footfall

```
monthly_sales = 446,410.58 + 35.68 × footfall
```

**R² = 0.7363** | **P-value = 4.75E-94**  Significant

**Coefficient Explanation:**
- **446,410.58 (Intercept):** If a store had zero footfall (no visitors at all),the predicted monthly sales would be £446,411. This is a baseline value and not practically meaningful on its own.
- **35.68 (footfall):** For every 1 additional customer who visits the store, monthly sales increase by £35.68 on average. So if footfall increases by 1,000 customers in a month, sales are expected to rise by £35,680.

**Business Meaning:** Store traffic is a very strong driver of sales.73.6% of the variation in monthly sales across stores can be explained simply by how many customers walk through the door.

---


## 2. Multiple Regression Equation

```
monthly_sales = 146,249.80
              + 33.68 × footfall
              + 1.18 × marketing_spend
              + 3,062.93 × inventory_availability_pct
              − 39,654.57 × Residential_dummy
              − 22,957.90 × HighStreet_dummy
              − 11,306.63 × Mall_dummy
```

**R² = 0.8199** | **Adjusted R² = 0.8165** | **Observations = 320**
**F-significance = 2.54E-113**  Highly Significant

---

## 3. Explanation of Each Coefficient

| Variable | Coefficient | P-value | Business Meaning |
|----------|-------------|---------|-----------------|
| Intercept | 146,249.80 | 0.0008  | Baseline monthly sales for an Airport store with zero footfall, zero marketing spend, and zero inventory availability. Not practically meaningful alone. |
| footfall | +33.68 | 1.23E-102  | Each additional customer visiting the store is associated with £33.68 more in monthly sales, after controlling for all other factors. |
| marketing_spend | +1.18 | 7.58E-18  | Each extra £1 spent on marketing is associated with £1.18 more in monthly sales. ROI is positive but modest. |
| inventory_availability_pct | +3,062.93 | 2.09E-10  | Each 1% improvement in stock availability is associated with £3,063 more in monthly sales. Stockouts are very costly. |
| Residential_dummy | −39,654.57 | 3.99E-05  | Residential stores earn £39,655 LESS per month compared to Airport stores on average, all else being equal. |
| HighStreet_dummy | −22,957.90 | 0.0152  | High Street stores earn £22,958 LESS per month compared to Airport stores on average. |
| Mall_dummy | −11,306.63 | 0.2510  | Mall stores appear to earn £11,307 less than Airport stores, but this difference is NOT statistically significant. Mall and Airport stores perform similarly. |

---

## 4. Explanation of Dummy Variables

Dummy variables are used to include **categorical (non-numerical) variables** in a regression model. They take a value of either 0 or 1.

**Store Type** had 4 categories: Airport, Mall, High Street, Residential.

We created 3 dummy variables:

| Dummy Variable | Value = 1 | Value = 0 |
|---------------|-----------|-----------|
| Residential_dummy | Store is Residential type | Store is any other type |
| HighStreet_dummy | Store is High Street type | Store is any other type |
| Mall_dummy | Store is Mall type | Store is any other type |

**Why only 3 dummies for 4 categories?**
Using all 4 would create perfect multicollinearity (the dummy variable trap), making the regression impossible to calculate correctly. So one category is always left out as the **reference category**.

---

## 5. Reference Category

**Reference Category = Airport Store**

Airport was chosen as the reference category because:
- Airport stores showed the highest average monthly sales in the dataset
- All other store type coefficients are interpreted **relative to Airport stores**
- This makes business sense — Airport stores are the premium benchmark

**Interpretation example:**
The Residential_dummy coefficient of −39,654.57 means:
*"A Residential store is expected to generate £39,655 less per month than an Airport store of similar footfall, marketing spend, and inventory."*

---

## 6. Final Model Selected

** Multiple Regression Model (Model 3) is the Final Selected Model**

```
monthly_sales = 146,249.80 + 33.68×footfall + 1.18×marketing_spend
              + 3,062.93×inventory_availability_pct
              − 39,654.57×Residential_dummy
              − 22,957.90×HighStreet_dummy
              − 11,306.63×Mall_dummy
```

---

## 7. Reason for Selecting the Final Model

| Reason | Detail |
|--------|--------|
| **Highest R²** | R² = 0.8199 vs 0.7363 (Model 1) and 0.1672 (Model 2). The multiple regression explains 82% of sales variation — significantly better than either simple model. |
| **Multiple business factors** | Captures footfall, marketing, inventory AND store type together — giving a complete picture rather than one factor at a time. |
| **Statistically strong** | 5 out of 6 predictors are statistically significant (p < 0.05). Overall model F-significance = 2.54E-113. |
| **Actionable for leadership** | The model directly answers the business questions: Should we increase marketing? Improve inventory? Focus on certain store types? |
| **Better than simple models** | Simple regression only looks at one variable at a time, which can be misleading. Multiple regression controls for all factors simultaneously, giving more reliable estimates. |
| **Practical R² improvement** | Going from R²=0.74 (footfall only) to R²=0.82 (multiple) means 8% more sales variation is now explained — a meaningful improvement for business planning. |